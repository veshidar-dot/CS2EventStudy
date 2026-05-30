# CS2 limited collections: event-study

Event-study on 6 CS2 collections after they were moved to limited (Shattered Web, Broken Fang, Armory).
Window [-30, +90] days from the event. Composite index (geometric mean) across 5-6 low-grade skins
per collection in Field-Tested wear. Skin names are pulled automatically from the open ByMykel CSGO-API
database; price history comes from the Steam Market price history endpoint.

## Key findings

- All 6 collections appreciate after going limited.
- Price peak lands on day +46 on average (median), with a tight cluster of +34...+52 that survives across two game engines (CS:GO and CS2) and three different operations.
- Volatility spike happens within the first 6 days post-event in all 6 collections.
- Graphic Design shows a two-stage "announcement + confirmation" response.
- Control, despite having the largest supply, also rises (+61 pp), just less than its sibling collection Havoc (+123 pp).

## Reproducing

1. Open in Colab via the badge above.
2. File → Save a copy in Drive (so you can edit it).
3. In the configuration cell paste your `STEAM_LOGIN_SECURE` cookie:
   F12 → Application → Cookies on steamcommunity.com → steamLoginSecure → Value.
4. Run all.

JSON responses from Steam are cached to `./cs2_cache/`, so subsequent runs are instant.

## Tunable parameters

- `WINSOR_PCT` (0.01) - winsorization of log-return tails before computing volatility.
- `SMOOTH_WINDOW` (5) - rolling-median window used when locating peaks.
- `MIN_DAILY_VOL` (3) - volume filter that excludes thin trading days from peak detection.
- `VOL_PEAK_WINDOW` ((0, 14)) - search window for the event-localized volatility peak.
- `USE_ANNOUNCE_AS_EVENT` (True) - whether to anchor Graphic Design on the announcement date instead of the actual removal date.

## License

MIT for the code, CC BY 4.0 for the text and figures.
