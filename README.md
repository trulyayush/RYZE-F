# RYZE hosted dashboard

RYZE is a private, static, browser-only fitness intelligence workspace. It has no backend, database, Kafka broker, WebSocket, external API dependency, or paid data dependency. Operational events, service health, partitions, offsets, facility occupancy, and short-range forecasts are generated synthetic data. The forecast page also includes a bundled public dataset of actual annual gymnasium attendance as a separate reference benchmark.

## Sample accounts

| Role | Username | Password | Access |
|---|---|---|---|
| Admin | `admin` | `RyzeAdmin!26` | Synthetic stream controls and dashboard |
| Viewer | `viewer` | `RyzeViewer!26` | Read-only dashboard |
| User 1 | `user1` | `RyzeUser1!26` | Read-only dashboard |

These sample credentials are included in the frontend bundle. The roles are for local interface access only, not secure authentication or authorization. The Site itself remains private and requires sign-in through its hosting platform.

## Local frontend
Run `npm ci`, then `npm run dev`. No external service is required. Build the static site using `npm run build`.

## Verification
- `npm run test:data` checks independent complete floors, unique objects, capacity bounds, aggregate counters, topic/key routing, sample offsets, stop and reset.
- `npm run test:ui` provides local Playwright interaction checks. Install its browser with `npx playwright install chromium` first.
- `tests/preview.html` is an isolated development-only component harness used to inspect desktop/mobile layouts. It is not included in the production output and has no authentication flow.

## RYZE redesign — 23 September 2026
- Same private Site project and URL; display title and application branding renamed to RYZE.
- Locally bundled Cinzel 700/800 and Cinzel Decorative 900; data labels retain readable sans-serif text.
- Continuous WebGL entrance sculpture with pause/reduced-motion support and animated artwork fallback when WebGL is unavailable.
- Horizontal desktop/mobile navigation, restyled dashboard, charts, cards, light theme and login.
- Detailed reusable fitness equipment models, reflective materials, improved lighting, humanoid instances, broker racks, forecast ribbons and wellness rings.
- Cleaner facility default with optional equipment, anonymous-avatar and screen layers; interactive zones and equipment keep utilization, occupancy and forecast details.
- Demand landscape follows the selected target and horizon, with matching one-hour, one-day, seven-day and thirty-day buckets.

## Browser-only operation
- Dashboard values come from a local synthetic fixture and in-browser simulation. The app makes no API or WebSocket requests.
- Admin, Viewer and User 1 sample accounts are available on the sign-in screen; Viewer and User 1 cannot change stream controls.
- Kafka, Spark, database, broker health, offsets and partitions are explicitly labeled as simulated examples; no services are running.

## Public fitness benchmark
- Bundled series: annual gymnasium attendances managed by Sport Singapore, 2012–2025.
- Publisher: Singapore Department of Statistics; source agency: Sport Singapore.
- Source: https://data.gov.sg/datasets/d_ed87f458933033c060cb5a548d1829d9/view
- Reuse: Singapore Open Data Licence. Values are cited and labeled in the forecast page.
- The public series is annual and aggregate. It is displayed as real-world context, not as hourly or gym-specific data, and does not drive synthetic short-range projections.

### Artwork provenance
Project asset: `public/ryze-strength-poster.webp`. Generated with the built-in image-generation tool, then encoded as WebP.
Prompt: Premium cinematic RYZE fitness-intelligence website background; no text or logos; wide 16:9 near-black graphite environment, realistic brushed titanium barbell with black plates and champagne-gold rims levitating over a circular architectural plinth; subtle smart-gym digital twin, treadmills, strength stations and fine gold data paths; restrained lighting and physically believable metal; dark negative space for copy and sign-in; avoid neon, gaming, humans and labels.

## Complete multi-floor facility — 24 September 2026
Every floor contains **cardio, strength, yoga, training and recovery**, with a separate layout, capacity, occupancy and inventory. The building contains 69 unique equipment objects (23 per floor); all six core machine types are available on every floor.

| Floor | Character | Additional specialty | Capacity |
|---|---|---|---|
| L1 · Everyday Club | Balanced training, cyan/slate | Sprint turf, push sled and agility ladder | 124 |
| L2 · Performance Lab | Strength and conditioning, warm amber | Olympic lifting platform and boxing bag | 128 |
| L3 · Restore Studio | Mindful movement, soft lavender | Pilates reformer and recovery pod | 120 |

- Building view shows all three furnished levels, with assembled/exploded modes and adjustable spacing.
- Select a floor tab or floor object to isolate it. Perspective, top and walk views, orbit/zoom, focus-on-selection, camera reset and fullscreen are available.
- Each floor has a permanent inspector with five zone selectors and its own equipment picker. Metrics stay scoped to the selected floor; aggregate overview metrics add all floors.
- Heatmaps show occupancy, equipment use or synthetic predicted demand. Equipment, labels, sampled people and motion can be toggled.
- Automatic non-WebGL fallback retains all floor, zone and equipment inspection controls. Mobile layouts place the inspector below the scene.
- Equipment inventory supports floor, state and ID filters.

## Stream explorer
- Six distinct interactive stage models represent sources, ingestion, illustrated Kafka brokers, processing, session storage and forecasts. Every stage explains its purpose, inputs and outputs.
- Twelve selectable partition objects and topic selectors filter the event inspector. The 2D pipeline retains stage inspection without WebGL.
- Recent events show their floor, source, topic, partition and accepted/flagged/rejected state. Select a record for its JSON payload, field units, key, sample offset, schema and synthetic delay.
- Pause particles affects animation only. Pause feed freezes the visible samples while the simulation continues. Clear filters restores all topic/floor/partition scopes.
- Topic directory describes all ten illustrated topics and their routing keys.
- Workload counters are projected, not a measured Kafka benchmark. Three example records are generated per 1.5-second update; the feed keeps 60 samples. Offsets count samples separately within each topic and partition from zero. A deterministic illustrative hash selects partitions; it does not implement a Kafka producer. Lag and processing delay are synthetic.
- All operational data is local simulation. The public annual attendance series is a separately attributed benchmark.

## Latest validation
The TypeScript/Vite production build and data regression checks pass. Managed-browser component checks cover isolated floors, specialty equipment inspection, topic/partition synchronization, payload inspection and feed freezing. A 390px mobile preview has no document horizontal overflow. The testing browser disables WebGL, so GPU geometry rendering and frame rate could not be visually verified here. Local Playwright tests are included for running on a machine with browser support.

## Download
The ZIP includes source, lockfile, assets, tests and built static output. Run `npm ci` then `npm run dev`; `npm run build` recreates `dist`. No backend is required.
