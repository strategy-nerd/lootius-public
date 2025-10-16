
# Change Log
All notable changes to this project will be documented in this file.
 
The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project mostly* adheres to [Semantic Versioning](http://semver.org/).

```
# [Template] - 2025-08-07
## Added

## Changed
### General

## Fixed

## Removed

---
```

# [1.3.3] - 2025-10-16
## Added
### Dungeon
- Added a toggle button for the dungeon console on mobile devices for easier access (bottom right corner of the main dungeon window).
- Ads | Introduced two ad banner types:
  - One banner specifically for non-mobile users, in between the dungeon main screeen and the inventory section.
  - One banner at the bottom of the inventory section.
  - **Both banners can be dismissed manually by users**
- Items | Added a new Mithril Shield item line.

<details>
 <summary>Mithril Shield Info</summary>
 
 ### Mithril Shield Line
 
**Crafting Costs:**
- Wood × 25  
- Metal × 25  
- Mithril × 10  
- Divine Essence × 100  

**Base Stats:**
- Tier: 2  

| Rarity        | Block Chance | Armor | Damage |
|----------------|--------------|--------|---------|
| Rusty Mithril Shield    | 4% | 3 | 0 |
| Mithril Shield          | 4% | 3 | 0 |
| Great Mithril Shield    | 4% | 3 | 0 |
| Imperial Mithril Shield | 5% | 3 | 0 |
| Marquise Mithril Shield | 5% | 3 | 0 |
| Royal Mithril Shield    | 5% | 3 | 0 |
| Legendary Mithril Shield| 6% | 4 | 0–2 |
| Eternal Mithril Shield  | 6% | 4 | 0–2 |

</details>

> [!IMPORTANT]
> Both ad banners on the dungeon page can be dismissed manually by users, and won't show up again until the page is reloaded or going to a different url and back

## Changed
### General
- Changed the background color site wide to align with our color pallete and improve readability of the text. (mostly in preperation for getting used the new ui).

### Dungeon Guide
- Updated and Clarified durability, item break logic, and loot pool explanations.

### Dungeon
- UI | Refactored inventory and equipment layouts for better usability and mobile support. 
  - Thanks to one of our community members DaineMudda for sharing his personal local changes (modified a bit to follow our linting rules).
- Item Break Logic
  - Standardized item destruction rolls (weapons, shields, rings, tools, trinkets) across all gameplay systems — ensuring consistent durability loss behavior.
  - More info for the reasoning at the bottom of this section.

- Balance Items & Npc's
  - Life drain has gotten a substantial boost to be more in line to what it should have been from the start. Life drain chance has been increased on the items that currently have it and life drain itself now has a multiplier, you can get upto 3x the damage you done back.
  - Vampiric Dagger | Adjusted max damage values to be more in line with the items in that tier. Adjusted lifedrain.
  - Vampiric Rapier | Vampiric Dust has been added to the crafting requirements (forgotton in the past) to be in line with the other items in this tier (dwarven mace). Adjusted lifedrain.
  - Battle NPC's | Crit damage & Rate Nerfed. 

<details>
 <summary>Item Balance Info</summary>
 
 ### Vampiric Daggers

| Rarity                   | Max Damage | Life Drain |
|---------------------------|------------------------|-------------------------|
| Rusty Vampiric Dagger     | 7 → 5                 | 3% → 4%                |
| Vampiric Dagger           | 7 → 5                 | 3% → 4%                |
| Great Vampiric Dagger     | 7 → 5                 | 3% → 5%                |
| Imperial Vampiric Dagger  | 7 → 5                 | 3% → 5%                |
| Marquise Vampiric Dagger  | 7 → 5                 | 3% → 5%                |
| Royal Vampiric Dagger     | 7 → 5                 | 3% → 5%                |
| Legendary Vampiric Dagger | 8 → 6                 | 4% → 6%                |
| Eternal Vampiric Dagger   | 8 → 6                 | 4% → 6%                |


### Vampiric Rapiers

**Crafting Costs:**
 - Vampire Dust 0 >>> 50

| Rarity                    | Life Drain |
|---------------------------|------------------------|
| Rusty Vampiric Rapier     | 4% → 6%                |
| Vampiric Rapier           | 4% → 6%                |
| Great Vampiric Rapier     | 4% → 7%                |
| Imperial Vampiric Rapier  | 4% → 7%                |
| Marquise Vampiric Rapier  | 4% → 8%                |
| Royal Vampiric Rapier     | 4% → 8%                |
| Legendary Vampiric Rapier | 5% → 10%               |
| Eternal Vampiric Rapier   | 5% → 10%               |

</details>

<details>
 <summary>NPC Balance Info</summary>

 ### NPC Balance (Battle NPCs)

| Mechanic | Old Behavior | New Behavior | Notes |
|-----------|---------------|---------------|--------|
| **Minaimal Critical Damage** | 1.6×  | 1.5×  | Reduced overall crit scaling; flatter curve for more damage distribution. |
| **Maximal  Critical Damage** | Dynamic  | - 25%  | Reduced maximum crit damage the calculation is still dynamic based on the npc, last version already reduced this a bit but the high ends were still way to high.    |
| **Critical Calculation** | Standard random roll | Smooth biasing model | Provides more predictable and tunable critical hit results. |

</details>

<details>
 <summary>Item Break Logic</summary>

### Unified Item Break System

Item durability and breakage have been standardized across all gameplay activities to create a consistent and predictable experience.  
This update aligns with our long-term gear design philosophy — encouraging strategic loadouts and risk management across all action types.

**Key Changes:**
- **Rings** now follow the same break rules as other gear types.  
  - Rings can **now break in every scenario**, regardless of activity.  
  - ⚠️ *Tip:* Avoid equipping valuable rings unless you plan to actively use them.  
- **Weapons, Shields, Tools, and Trinkets** have been updated to follow the unified breakage model.  
- All item groups now share consistent durability logic across combat, gathering, and crafting services.  

| Item Group | When It Can Break |
|-------------|-------------------|
| **Battle Gear (Weapons & Shields)** | Chance to break on every used action during a battle instance. |
| **General Gear (Rings – Left & Right)** | Chance to break on every used action, regardless of activity. |
| **Woodcutting Gear (Axes)** | Chance to break on every used action in a woodcutting instance. |
| **Mining Gear (Pickaxes)** | Chance to break on every used action in a mining instance. |
| **Keys** | Chance to break upon successfully defeating an NPC or gathering from a keyed area. |
| **Trinkets** | Break based on specific trigger actions (see below). |

**Trinket Break Conditions:**
- **XP Trinkets** → Chance to break when experience is gained.  
- **Crafting Trinkets** → Chance to break on every crafting attempt.  
- **Lootius Trinkets** → Chance to break on every loot attempt.  
 
### Developer Notes

> *"We wanted a unified system that could support all the new gear progressions we’re planning.  
> This ensures consistency across every activity — whether you’re battling, crafting, or gathering.  
> The update also lays the foundation for future gear expansions, including new left-hand rings that can influence all action types."*  
> — **Caimen**

We’ve made changes to bring **rings** in line with a more unified **item break system**.  
Rings can now break in every scenario — just like other gear types.  
Our advice: **don’t equip anything you aren’t willing to lose.**

This update reflects our long-term design philosophy.  
We want the **core strategy** of the game to revolve around **how you prepare and equip your character** for different activities.  
Your setup, and the risks you choose to take, should be a meaningful part of your decision-making — not just your stats or level.

We’re also preparing for **new left-hand rings** and **future gear systems** that can affect multiple action types, not just combat or gathering.  
To make this possible, we needed a **consistent, predictable durability model** that works across all gear and activities.

Behind the scenes, we’ve been **mapping out item stats, attributes, and gear progressions** across all current and future tiers.  
This groundwork helps ensure that every new item we introduce fits logically into the broader system — keeping gear progression **balanced**, **rewarding**, and **future-proof**.  
It also ties into our upcoming plans for **expanded crafting, upgrading, and new progression paths**, giving us the flexibility to build deeper itemization without breaking existing systems.

Ultimately, this unified break logic is a key part of **future-proofing the game**.  
It maintains fairness across all activity types and ensures that gear — from your first weapon to your endgame relic — follows the same consistent, strategic rules.

</details>

> [!NOTE]
> *"We wanted a unified system that could support all the new gear progressions we’re planning.  
> This ensures consistency across every activity — whether you’re battling, crafting, or gathering.  
> The update also lays the foundation for future gear expansions, including new left-hand rings that can influence all action types."* 

### Store
The store has been changed in how it works as we got a new giftcard provider which gives us more freedom in what we can offer and what values we can offer. All giftcards are now on demand instead of instant purchase and we will email the key within 48 hours (usually witin 24). We are also looking into options for the EU region.

- Revamped gift card, Tibia, and Wizard101 purchase flows.
- Added variable USD value support, you can now select between values between 25-100 in increments of 25 
- Updated purchase and confirmation views for better clarity.
- Improved admin notifications and user messaging during transactions.

## Fixed
- Dungeon UI | Damage clipping, Damage now displays the correct values when hit at low hp. previously it would show all damage even if that would get you to negative hp.
  - previous: hp 1 > damgae calculated at 10 > ... hit you for 10 damage, a critical hit > 0 hp.
  - current: hp 1 > damgae calculated at 10 > ... hit you for 1 damage, a critical hit > 0 hp.
- Rewards | prevented referrers from seeing a chargeback in the user actions when a user they refferec has an offer being charged back
- Account Profile | minor ui display errors in the action log (mainly rewards).
Offerwall | Fixed incorrect offerwall and crate hunt messages.

## Removed
- Ravendawn references across the site as we no longer support purchases for this title.
- The ability to purchase giftcards when havign a negative balance (whoops).
---


# [1.2.0] - 2025-08-07
### Added

### Changed
- Crate Hunt | Crate Hunt no longer triggers automatically upon opening the page. A confirmation box with a button has been added to help combat bot usage.
- Crate Hunt | Updated the drop probability table to display more trailing digits, increasing precision.

### Fixed
- General | Fixed numerous small bugs.

### Removed
- Offerwall | Removed the AdGate offerwall as our partnership with them has ended.
---


# [1.1.1] - 2025-07-18
### Added
- Crate Opening | Currency crates now have their own dedicated animated opening page.

### Changed
- Dungeon Crates | Dropped items from dungeon crates now appear in the dungeon log.
- Crafting Probability Changes | Crafting success rates have been slightly buffed — especially noticeable at higher crafting levels, though the changes apply from level 1 to 100.
- Logging | Minor logging changes and preparations for future updates.

### Fixed
- Offerwall | The bug caused by a stray `)` in the Lootably callback has been fully resolved.
- Memory Leak | Small memory leaks in several UI areas have been fixed. There may still be some remaining — if you notice unusually high memory usage, please report it on Discord.

### Removed
- Crate Opening | Removed the ability to open currency crates directly from the dungeon. This feature was only intended as a temporary system.
---


# [1.0.3] - 2025-06-26
### Added

### Changed
#### Dungeon
- NPC Scaling | NPC Crit Damage scaling has been nerfed a bit.
  - Lower crit multiplier has been lowered to 1.6x
  - Upper crit multiplier is stil dynamic but on average is about 20% lower.
- UI | Swtiched console messages around, user is now left and nps right.
- UI | Adjusted the  Legendary and Eternal item borders, with a bit less spread. 

### Fixed
#### General
- Offerwall | Fixed a bug causing CPX offer completions not to be rewarded / displayed.
  - All offers from the prior period have been retroactively awarded. 
- Withdraw UI | Fixed the date display to account for new server time change from CST to UTC in [v1.0.0](#100---2025-06-13)
#### Dungeon
- Fixed a bug that caused multiple users to target the same NPC, instead of acting on one's own NPC.
- Market | Fixed a bug that caused item amount to be overwritten instead of being added to the exisitng amount.

### Removed
---


# [1.0.2 Hotfix] - 2025-06-15
### Added

### Changed
#### General
- Withdraw & Deposit
  - Deposits are now accepted again.
    - **Note: We reserve the right to refuse deposits for any reason.**

### Fixed
#### General
- Offerwall | Fixed a link endpoint that caused a 5xx response.
- Offerwall | Fixed a validity check that threw a uncaught error.
#### Dungeon
- Fixed a bug that caused multiple users to target the same NPC, instead of acting on one's own NPC.
- Market | Fixed a bug that caused item amount to be overwritten instead of being added to the exisitng amount.

### Removed
- Dungeon UI | Removed redundant "Action Complted" console log message from testing.
---


# [1.0.1 Hotfix] - 2025-06-14
### Added

### Changed
- Updated logging levels in multiple places.

### Fixed
#### General
- UI | Fixed Testing watermark displaying on live version.
- Offerwall | Fixed RevU completed offers not displaying on user profile.
#### Dungeon
- Crafting | Fixed a bug that caused potions to be uncraftable.
---


# [1.0.0] - 2025-06-13
> [!NOTE]
> **Oh boy, it’s finally here.**  
> It took some time, but for good reason!  
> The codebase has been almost completely rewritten (UI excluded) on a modern, scalable framework. This unlocks a streamlined development pipeline moving forward, meaning we can now focus on specific game features, faster iterations, and cleaner updates.
> 
> This rewrite wasn’t just a luxury—it was a necessity. The old server and architecture were on their last legs. We couldn't keep our promised 3-second game tick; the system would often grind to 6+ seconds.
> 
> Worse, the backend had grown into a tangled mess: one giant loop, blocking logic, no proper async handling, and no separation of concerns. **That said, this kind of technical debt builds up naturally—especially in long-running projects.**  
> Every small change risked breaking unrelated systems, and adding new features took far too much time.<br><br>
> Nika / Nikander

### Added
#### General
- Versioning | Version is now displayed below the logo and in the footer with the release date.
- Authentication
  - Login page has been added with proper "Remember Me" support — no more surprise logouts after server restarts!
- Offerwall
  - Revenue Universe has been added with a wide variety of offers.
#### Dungeon
- Loot Tables | All NPCs now use dynamic loot tables with min/max drop values and percentage-based drop chances.
  - Enables rare loot, multiple drops, and variable resource yields.
- NPC Scaling | NPCs now scale stats like block, crit, dodge, and armor based on their tier.
  - Block, Crit Chance, and Dodge Chance now scale dynamically.
  - Crit Damage is no longer fixed at 2x — it now ranges from x1.6 to a dynamic upper limit based on tier.
  - Armor has a dynamic range between 0 and the NPC’s tier.
  - To balance these changes, low-tier NPCs now drop 1–2 items (previously only 1).
- Market
  - Offers & Orders now expire after a 30-day period and can be reclaimed.
    - Expired orders are highlighted on the `Market > My Orders` page.
  - Orders can now be partially filled.
    - Example: A 10k Metal order can be filled with just 1k from your inventory; the rest stays open.
    - You can't yet specify an exact amount to sell.

### Changed
> [!IMPORTANT]
> As this is a full rewrite, most of these changes are UI or structure related. New features are listed above in the [Added](#added) section.

#### General
- New Server | We've moved off the old server to a higher-performing one!
- Timezone Changes | The new server runs on UTC, making it easier to support global users.[^2]
- Authentication
  - We’ve migrated to full ASP.NET Identity-based authentication — streamlining login, logout, and authorization.
- User
  - Login | Now lives on its own dedicated page: `lootius.io/login`[^1]
  - Registration | Updated to allow manual entry of referral codes and includes a short intro about Lootius.
    - Referral links are remembered for 1 hour even if you leave and return later.
  - Account | User profile moved to `lootius.io/user/account` (and soon also accessible via `lootius.io/account`).[^2][^1]
    - The page is now more mobile-friendly.
    - Crate opening via the account page has been temporarily removed, but will return soon.
- Hall of Claims | Statistics are now cached for 30 minutes (claims still update instantly).
- Ranking | Rankings are cached for 30 minutes — so newly leveled players may not appear instantly.
- Offerwall
  - Minor UI bugfixes applied — nothing major to report.
- Terms of Use & Privacy Policy
  - Updated support email and switched date format to be timezone-neutral.
  
#### Dungeon
  - Dungeon UI | Item glow toned down to prevent visual overlap. Log messages (especially for market and NPCs) were cleaned up.
  - NPCs | Low-tier battle NPCs now drop 1–2 items to better balance against stat scaling changes. See [Added](#added).
- Market | Sell offers now show with market fee included.
- Crate Opening | Due to the urgency of the release the user interface for opening crates has not yet been finished. The crate opening page will come back shortly. 


### Fixed
- A lot of bugs — like, a jar full of them!!  
  Most were niche edge cases, but some major issues simply couldn’t be fixed in the old architecture.  
  Since this release is a complete rewrite, listing every bug fixed would be irrelevant — and let’s be honest, there are probably new ones lurking in the dark corners of the dungeon... ready to ambush us.

[^1]: In preparation for migrating to the new frontend.
[^2]: In preparation for public profiles and expanded user settings (e.g. linking OAuth logins, setting location/timezone, display name, and preferences like "stop salvaging when below X items" and dont step down values "selected salvage 25x wont salvage if only 20 items left.").
---


# [0.9.1] - 2024-04-30
 
### Added
   
### Changed
- Dungeon Guide | updated section about ring usage and fixed multiple typos.
- Withdraw Page | Re-removed Deposit Section. Deposits are currently halted until further notice.
 
### Fixed
 
- Dungeon Ui | MINOR Fix  Re-added missing stamina and health text.
- Offerwal/PixelpointTV | MINOR Fix  ppTV still tried to make use of the viewbag instead of the ViewModel, which made the page render blank.
---


# [0.9.0] - 2024-04-28

> [!NOTE]
> This is my first big addition since joining the Lootius team as (junior)developer, over the previous year I have helped purely with withdraws. I have learned a lot over the past month about the project and the codebase. It might not look like much has changed but a lot has changed behind the scenes :) I hope to deliver more, and more efficient updates in the future when I am more settled down with the project. <br><br>
> Nika / Nikander
 
### Added

- Inventory Sorting | Tabs have been added to the inventory to sort the items based on type. Current tabs are `All`, `Tools / Stamina Potions`, `Weapons / Armor / Hp Potion`, `rings / trinkets`, `crafting materials`.

- Inventory Search | A search bar has been added to the inventory allowing to search for specific items. A search can be a exact item name but also partually. If you type in `great` you will see all your great-tier items.
   
### Changed

- JavaScript | All JavaScript has been completely Refactored and made more dynamic. The original JavaScript was all over the place or embedded in the HTML files, which made it unclear what did what. Most of the JavaScript has been moved to its own respective files.

- CSS/Styling | Same goes for the CSS/Styling. Most of it was embedded into the HTML files, making it unclear what was affecting what at times and also making it redundant, so a part of the code was duplicated where it could have been done more efficiently. 

- User Registration | Leading and trailing spaces trimmed of username and game account names. Updated the input field with the required tag so that the forum cannot be accepted if the required data is missing and added confirmation boxes for the Terms of Service, etc.

- Unauthenticated Users | Users that are not logged in will now be displayed a not-logged in page when trying to access certain parts of the site. `dungeon`, `store`, `offerwall`, `cratehunt` and `profile`.

- Offerwall | Offerwall index page has undergone a complete Refactoring from mostly hard-coded to completely dynamic, making it easier to add, update, or remove offerwalls. All our partnered offerwalls have each gotten their own sub-page on the offerwall. They used to be on the index page, but with a slow connection, they would take a long time to load.

- Logout Page | Logout page recieved minor visual changes. Auto redirects you to the homepage 2 seconds after a successful logout.

- #### Dungeon UI
  - The dungeon page has been partially refactored; a lot of HTML code has been cleaned up and is easier to work on from now on. The JavaScript for buy and sell orders has also been completely rewritten to be more flexible for future changes.

  - The dungeon UI has received some minor style updates. With the changes to the JavaScript, it became a lot easier to implement styling for the console messages. Thus, there are a lot of new colors added to make certain messages stand out more. Some are: out of HP/stamina, higher rarity item crafts, salvaging, market offers and orders, and more.
  - The Dungeon and Action windows now have borders, making them a bit more friendly to look at. The action window doesn't have scrollbars anymore but could be added back in a future update. (On a PC, to scroll down quickly, press down your scroll wheel while having your pointer over the action window.)

  - Inventory items are spaced out a little bit; previously, borders would overlap.

  - Confirmation dialogs have been added for `Action Boost`, `Dungeon Chest` and `Levelup` making accidental purchases almost impossible now.

- Dungeon Guide | The Guide has been refactored from a big part hard-coded to as good as fully dynamic, except the index. It has also been made more mobile-friendly. Items show the required skill and crafting level. Stats per quality are also shown. The crafting calculator only displays if an item is craft-able. <br> There will most likely be another update in the near future that will update the general guide.

- Land Area | Small styling updates. Added a disclaimer that any globals registered before account registration do not count for any rewards.

- #### Dungeon Sevice (The Game)
  - Added multiple checks if a player cannot continue an action due to multiple reasons: `out of hp`, `out of stamina`, `out of materials` and `required level` If any of these are true, all remaining actions will be set to 0, and a message will be displayed in the action log. <br>This change has made a bit of a difference in the lag that there currently is. When there are around 55 people actively playing, the actions are around 0.5 seconds quicker. When around 80 people are actively playing, actions are around 0.2 seconds quicker than before.
  - Updated the salvaging output text to be clearer in what has been salvaged and what has been used.
  - Item Durability | Over the past month, we have tested higher item durabilities, and based on the data, we have adjusted some back down.
    - Marquise Tier has been lowered back to its original value from before testing. 100K Durability.
    - Royal tier are now 5 million durability instead of 10M. (still 5x as much as before 😎)
    - Legendary tier will stay at 100 million.


 
### Fixed
 
- Dungeon MINOR Fix | Experience going into the negative when double-clicking the button should be fixed now. If this still occurs, please let me know `@nikander100` on Discord.
---
