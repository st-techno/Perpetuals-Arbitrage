# Perpetuals - Arbitrage Bot
This is an arbitrage bot that can be run on AWS Lambda (works with free tier) or locally. The bot allows to execute automated trading strategies between Perpetual Protocol and FTX.

Since Perpetual Protocol runs on xDai, you can use this bot entirely without paying gas fees on Ethereum. Gas fees on xDai are very low (1 Gwei).

# Default Strategy
The default strategy is to "buy low, sell high" to make profit between two different exchanges. For example, most of the time, the price of ETH-PERP at Perpetual Protocol and FTX will be similar. However, price action on the exchanges leads to price differentials from time to time. This bot is designed to open positions when the price difference (spread) is greater than a set level, and to close the positions when the spread decreases below a set level. 

For example, when the ETH-perp on Perpetual Protocol is 1500, and 1520 at FTX, we could long ETH-perp at Perp exchange, and short at FTX in the expectation that some time later the prices will converge. Let's say the price at Perpetual Protocol increases to 1550, and the price at FTX increases to 1555. The bot will sell the positions at both exchanges. The PnL in this example will be +50 USD on Perpetual Protocol, and -35 USD at FTX, for a total of +15 USD. 

After some setup, by adjusting `PERPFI_SHORT_ENTRY_TRIGGER` and `PERPFI_LONG_ENTRY_TRIGGER`, arbitrage between Perptual Protocol and FTX. 

Note that there are many parameters which can be adjusted based on our own risk apetite such as leverage, trigger conditions, exit conditions, etc. 
