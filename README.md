# Trend Is Your Friend

These trend-following strategies uses multiple moving averages to identify the direction of the trend and trigger entry signals. We don't get bottom or top of the trend but our goal is get most of the long trends.

My main indicator, [Trend is your friend](./Trends.pine), combines four different moving averages with pullback recognition, PDH and PHL levels and some risk management rules to form a complete trading system.

The strategy was created and is maintained by [Timo Anttila](https://timoanttila.com/). It's free to use and modify, and I encourage collaboration - let's improve this script together instead of creating separate versions. If you have suggestions or ideas, feel free to reach out.

This indicator is built for [TradingView](https://www.tradingview.com/), a widely used platform for technical analysis and trading.

## Moving Averages

A moving average smooths price data over time to help identify trend direction by filtering out short-term noise.

A Simple Moving Average (SMA) gives equal weight to all data points and reacts slower to price changes, which makes it more stable. It's better for identifying longer-term trends.

An Exponential Moving Average (EMA) gives more weight to recent prices, so it responds faster to changes but can produce more false signals. It's more useful for short-term trends.

Shorter moving averages react quickly but may generate more false signals. Longer ones are more stable but slower to respond.

## Strategy Overview

| Key | Length | Type | Color | Description |
| --- | --- | --- | --- | --- |
| `m1` | 10 | EMA | Aqua | Crossover / Soft exit |
| `m2` | 20 | SMA | Orange | Crossover / Hard exit |
| `m3` | 50 | SMA | Yellow | Base for trade entries and filtering |
| `m4` | 200 | SMA | White | Strong support or resistance |

This trading strategy is inspired by the famous [Turtle Trading](https://www.investopedia.com/articles/trading/08/turtle-trading.asp) methodology for trend identification.

Buy or sell signals happen when `m1` crosses over or under `m2` and both moving averages are above `m3`. There can also be early entries when `m1` crosses `m2` but `m3` is still against the trade. For a valid signal, the candle must have a body that's at least 40% of its total size and must close above or below the last four candles, depending on the direction. This helps reduce false signals.

Adding to strong trends can boost profits. Even with a low win rate, large gains on winning trades can outweigh small losses. The goal isn't to be right every time but to make more when you're right.

The first color change with an opposite candle offers a chance to add to a winning trade. When a new candle breaks the pullback candle's high for a bullish trend or low for a bearish trend, a `cross` icon appears. This suggests the pullback may be over and the trend could resume in its original direction.

If you add to your position, it's wise to move your stop loss to your new entry level or just below a key level. A common approach is placing the stop under the most recent pullback or consolidation area.

## Risk Management

This strategy works well in trending markets but tends to give more false signals during ranging conditions. Candle validation helps filter out some of the bad signals, but it doesn't eliminate all of them. That's why it's important to observe the direction of the candle that follows the signal candle and stay aware of any strong support or resistance zones nearby.

The key to long-term success is solid risk management. Cut losses quickly and let winners run as long as the price stays above `m1` or `m2`. Using a trailing stop loss can help lock in profits as the trade moves in your favor.

Your initial risk should be no more than 1% of your account. After additional entries, total risk should stay under 2%. Because you'll be wrong often, managing your risk is what keeps you in the game.

Avoid trading against the direction of `m3` and `m4`. If those moving averages are close to your entry, it's better to wait for a clear price reaction. The best entries usually come after a breakout followed by a successful retest.

## Alerts

You can set alerts for different scenarios: new entry signals only, new plus additional entries, or direction-specific alerts.

## Optimization

The moving averages and signal rules can be adjusted to fit different markets or timeframes. You can increase the minimum body percentage to reduce signals, or tweak the candle count used for highs and lows based on how volatile the market is.

Make changes for logical reasons, not just to fit past data. The default settings offer a solid starting point, but different situations may call for adjustments.