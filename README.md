# tetrider's Craft from Stashes

An adaptation of [Craft from Stashes](https://www.moddb.com/mods/stalker-anomaly/addons/craft-from-stashes) for the GAMMA modpack.
Reduces loot micromanagement during crafting, repairing, and artifact empowerment — all workshop operations can use items from nearby stashes (default range: 10m), configurable via MCM.

## Covered systems

- Workshop (craft, repair, upgrade) — toolkits, repair kits, weapon/armor parts, and upgrade kits are all pulled from nearby stashes
- Quick repair (item_repair) — the menu opened when using glue or sewing kits; repair materials are pulled from nearby stashes
- Artifact melter (grok_artefacts_melter)
- Cooking (separate MCM range, default 50m)

## Item priority during crafting

When consuming degradable items, the mod picks **lowest condition first**.

**Exception: artifacts** use **highest condition first** (optionally).

**Exception to the exception: perk artifacts** (`af_signet`, `af_pas`) always use lowest condition first.

## Difference from [Demonized's](https://www.moddb.com/mods/stalker-anomaly/addons/universal-craft-repair-cook-from-stashes)

- **Demonized's** injects an `OwnerAggregate` class that replaces `db.actor` via metatable, tricking vanilla scripts into seeing stash inventories transparently. It also consolidates partial ammo stacks across stashes at UI open time.

- **This mod** uses monkey patching — directly overrides individual functions in each crafting script. More verbose, but covers artifact melter (not in Demonized's) and extends `craft_use_low_cond`'s condition-based priority to nearby stashes.

**Do not run with original or demonized's simultaneously.**
