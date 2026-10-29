# Trading Strategy Automation

A TradingView strategy I built around the Asian session range and the London session that follows it. The idea is simple: let Asia set the range overnight, watch for London to break it, then only take a trade when market structure breaks back the other way.

## How it works

- **Asian session (22:00–03:00 New York time):** the script boxes the session and tracks its high and low.
- **London session (03:00–08:00 New York time):** it marks a break of the Asian high or the Asian low. The first break wins, and the other level's line is removed.
- **Market structure:** after a bullish break it tracks higher highs and higher lows; after a bearish break it tracks lower lows and lower highs.
- **Entry:** one trade per London session, on the first break of structure — a close below the most recent higher low after a bullish break (short), or a close above the most recent lower high after a bearish break (long).
- **Stop and target:** the stop is the London session extreme, or an ATR multiple if that option is turned on. The target is the opposite Asian extreme.
- **Position sizing:** USD risk per trade or a fixed number of contracts.
- **Session rules:** no new trades in the last 60 minutes of London (adjustable), and open trades are closed at the end of London if force close is on.

## How to use it

1. Open the Pine Editor in TradingView and paste in `trading-strategy-automation.pine`.
2. Add it to the chart. I run it on a 15-minute chart.
3. Session hours, timezone, ATR settings, risk per trade, and colors are all adjustable in the script settings.

## Files

- `trading-strategy-automation.pine` — the full strategy script

This is a strategy I built for my own charting and backtesting, not financial advice.
