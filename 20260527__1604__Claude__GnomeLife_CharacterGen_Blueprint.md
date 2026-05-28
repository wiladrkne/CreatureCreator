# 🍄 GnomeLife Character Prompt Generator
## Work Order & Blueprint — Shared Frequency Mobile Edition

**Project:** GnomeLife Character Generator v2 — Dark Mobile  
**Target Platform:** Mobile browser (375–430px viewport)  
**Aesthetic Reference:** Shared Frequency — Gothic-Roman cinematic dark neon  
**Input Method:** Dropdowns (replaces checkbox grids)  
**Status:** Ready to build in new chat  

---

## 1. WHAT WAS BUILT (v1 Reference)

The desktop version (`Character_Generator.html`) is a fully working 12-step character prompt generator that:

- Accepts trait selections across 12 pipeline cards
- Assembles them into a structured Meta AI–safe prompt in real time
- Supports Lock/Unlock per card to protect selections from Random
- Clear All respects locked cards
- Saves up to 5 prompts to a collapsible history panel with Copy, Restore, Delete
- Random rolls 1 trait for singlePick cards, 1–3 for multi-pick cards

---

## 2. THE 12-STEP PIPELINE (exact keys, labels, behavior)

| Step | key | Label | singlePick | Notes |
|------|-----|-------|------------|-------|
| 1 | `creature` | Mythological Creature | ✅ | Subject of the prompt. Gnome = hero. Others = background legend |
| 2 | `scene` | Scene / Setting | ✅ | Location sentence |
| 3 | `backstory` | Home / Backstory | ❌ | Origin clause |
| 4 | `personality` | Personality | ❌ | Drives article grammar (a/an) |
| 5 | `appearance` | Appearance | ❌ | Face description |
| 6 | `hair` | Beard / Hair | ❌ | Physical character |
| 7 | `hat` | Hat Style | ❌ | Headwear |
| 8 | `outfit` | Outfit / Clothing | ❌ | Clothing |
| 9 | `skills` | Skills / Talents | ❌ | Mastery sentence |
| 10 | `companion` | Pet / Companion | ❌ | Companion sentence |
| 11 | `lighting` | Lighting / Mood | ✅ | Atmosphere sentence |
| 12 | `renderstyle` | Visual Style / Render | ❌ | Style tail (Burtonesque, 8K, etc.) |

---

## 3. PROMPT BUILDER LOGIC (sentence order)

The output textarea assembles sentences in this exact sequence:

```
S1  [article] [personality...] [creature] — a [backstory...]
S2  The [creature] has [appearance], [hair], wearing a [hat], dressed in [outfit].
S3  Known for their mastery of [skills].          (omit if empty)
S4  Accompanied by a loyal [companion].            (omit if empty)
S5  Set in a/an [scene].                           (omit if empty)
S6  A/An [creature] looms in the distance...       (omit if creature = Gnome or empty)
S7  The scene is bathed in [lighting].             (omit if empty)
S8  Fantasy storybook art... Rendered in [renderstyle] style.
    (fallback: "...vibrant color palette, 8k resolution." if renderstyle empty)
```

**Grammar rule:** article before S1 is `"an"` if first personality trait OR creature starts with a vowel, else `"a"`.

---

## 4. CARD BEHAVIOR RULES

- **singlePick cards** show a gold `1 on Random` badge
- **Lock button** shows current state: `🔓 Unlocked` → click → `🔒 Locked`
- **Locked card** visual: blue-tinted border (`#1e3a5c`), blue title, checkboxes/selects at 55% opacity
- **Random** skips locked cards entirely, does NOT clear their selections
- **Clear All** skips locked cards entirely
- **History** saves up to 5 prompts. Buttons per entry: 📋 Copy, ↩ Restore, ✕ Delete
- **History panel** auto-opens on first save, collapsible toggle with entry count badge

---

## 5. FULL TRAIT DATA

### Step 1 — Mythological Creature (singlePick)
```
Gnome, Dragon, Phoenix, Griffin, Minotaur, Centaur, Mermaid, Kraken, Cerberus, Chimera,
Manticore, Pegasus, Sphinx, Basilisk, Wyvern, Yeti, Banshee, Kitsune, Troll, Goblin,
Leviathan, Wendigo, Selkie, Naga, Dryad, Fenrir, Thunderbird, Nixie, Cockatrice, Djinn, Tanuki
```

### Step 2 — Scene / Setting (singlePick)
```
Enchanted Forest, Ancient Ruins, Mushroom Cavern, Tidal Cliffs, Sunlit Meadow,
Frozen Tundra, Volcanic Crater, Floating Islands, Underground Library, Misty Swamp,
Crystal Grotto, Haunted Village, Celestial Observatory, Coral Reef Kingdom, Desert Oasis,
Stormy Mountaintop, Bamboo Grove, Cursed Battlefield, Fairy Ring Clearing,
Glowing Bioluminescent Jungle
```

### Step 3 — Home / Backstory
```
Forest Dweller, Mountain Clan, River Village, Meadow Explorer, Cave Dweller,
Garden Keeper, Library Scholar, Traveling Cart, Mine Worker, Coast Dweller,
Village Baker, Royal Guard, Wandering Bard, Hermit, Caravan Trader,
Shipwright, Temple Monk, Star Gazer, Reclusive Artist, Guardian of Ruins
```

### Step 4 — Personality
```
Kind, Curious, Brave, Cheerful, Shy, Mischievous, Wise, Loyal, Playful, Patient,
Adventurous, Creative, Dreamy, Grumpy, Optimistic, Humble, Stubborn, Generous,
Hardworking, Quirky
```

### Step 5 — Appearance
```
Rosy Cheeks, Freckled Face, Round Nose, Pointy Ears, Twinkling Eyes, Wrinkled Smile,
Chubby Face, Sharp Eyes, Long Eyelashes, Thick Eyebrows, Youthful Face, Weathered Skin,
High Cheekbones, Button Nose, Dimples, Sparkling Eyes, Gentle Expression,
Strong Jawline, Soft Features, Mischievous Grin
```

### Step 6 — Beard / Hair
```
Long White Beard, Short Beard, Braided Beard, Curly Beard, No Beard, Wild Hair,
Bald Head, Red Beard, Grey Beard, Mustache, Twin Braids, Ponytail, Dreadlocks,
Flowing Hair, Spiky Hair, Sideburns, Top Knot, Buzz Cut, Long Brown Hair, Golden Beard
```

### Step 7 — Hat Style
```
Pointy Hat, Knit Cap, Leaf Hat, Mushroom Cap, Hooded Cloak, Patchwork Hat, Bell Hat,
Tall Wizard Hat, Slouchy Beanie, Flower Crown, Straw Hat, Adventurer Hat, Hood with Ears,
Pilgrim Hat, Nightcap, Leather Cap, Crown of Twigs, Chef Hat, Miner Helmet, Decorated Cap
```

### Step 8 — Outfit / Clothing
```
Farmer Overalls, Ranger Cloak, Wizard Robes, Blacksmith Apron, Adventurer Gear,
Herbalist Wraps, Tailor Vest, Miner Overalls, Fisherman Coat, Baker Outfit,
Druid Robes, Leather Armor, Patchwork Clothes, Royal Garb, Scholar Robes,
Gardener Apron, Cook Apron, Steampunk Coat, Simple Tunic, Explorer Outfit
```

### Step 9 — Skills / Talents
```
Gardening, Cooking, Alchemy, Blacksmithing, Woodworking, Fishing, Mining, Foraging,
Tailoring, Brewing, Storytelling, Magic, Healing, Tracking, Pottery,
Music, Painting, Animal Care, Engineering, Mapping
```

### Step 10 — Pet / Companion
```
Fox, Rabbit, Squirrel, Hedgehog, Owl, Badger, Cat, Dog, Bird, Deer,
Frog, Toad, Mouse, Butterfly, Turtle, Goose, Goat, Dragonfly, Bee, Snail
```

### Step 11 — Lighting / Mood (singlePick)
```
Golden Hour, Moonlit Fog, Candlelight Glow, Thunderstorm Ambience, Soft Dawn Light,
Dappled Forest Sunlight, Bioluminescent Glow, Twilight Haze, Overcast Diffused Light,
Firelight Flicker, Northern Lights, Harsh Midday Sun, Deep Shadow Contrast,
Underwater Caustics, Volcanic Ember Glow, Misty Morning Light, Starlit Night,
Lantern Warm Glow, Eclipse Light, Ethereal Bloom
```

### Step 12 — Visual Style / Render
```
Burtonesque, Pixaresque, Miyazaki-esque, Disney Classic, Dark Fantasy,
Watercolor Wash, Oil Painting, Ink Sketch, Comic Book, Storybook Illustration,
Volumetric Light, Ray Traced, Subsurface Scattering, Depth of Field, Bokeh Background,
Tilt Shift, Macro Close-up, Full Body Shot, Portrait Framing, Wide Cinematic Shot,
4K Resolution, 8K Resolution, Ultra HD, Hyperrealistic, Cinematic Grade
```

---

## 6. SHARED FREQUENCY AESTHETIC (v2 Design Spec)

### Color Palette
```css
--bg-deep:       #0a0a0f   /* page background — near black */
--bg-card:       #0f0f1a   /* card surface */
--bg-card-hover: #131320   /* card hover state */
--border:        #1a1a2e   /* default card border */
--border-accent: #00ffff33 /* teal glow border (locked / active) */
--text-primary:  #e0e0ff   /* soft lavender white */
--text-secondary:#8888aa   /* muted secondary */
--text-dim:      #44445a   /* disabled / placeholder */
--accent-teal:   #00e5ff   /* primary neon teal */
--accent-cyan:   #00bcd4   /* secondary cyan */
--accent-magenta:#e040fb   /* magenta highlight */
--accent-gold:   #ffd700   /* gold for GnomeLife brand */
--locked-bg:     #0a0a1f   /* locked card bg */
--locked-border: #00e5ff44 /* locked card border glow */
```

### Typography
- Headers: `'Cinzel'` or `'Playfair Display'` (Google Fonts) — Gothic-Roman serif
- Body/labels: `'Inter'` or `'Segoe UI'` — clean sans-serif
- Monospace output: `'Fira Code'` or `'Courier New'`
- Title size: `1.8em` on mobile
- Label size: `0.82em`

### Visual Effects
- Cards: `box-shadow: 0 0 12px #00e5ff1a` on hover
- Locked cards: `box-shadow: 0 0 16px #00e5ff33`, teal border glow
- Active dropdown border: `1px solid #00e5ff` with subtle glow
- Buttons: teal/magenta gradient or solid teal with hover glow
- History panel: dark glass effect — `background: #0a0a1f`, `backdrop-filter: blur(4px)`

---

## 7. MOBILE UX CHANGES (v1 → v2)

| Feature | v1 Desktop | v2 Mobile |
|---------|-----------|-----------|
| Input method | Checkbox grid (2 col) | `<select>` dropdowns |
| singlePick cards | Checkbox, 1 forced on Random | `<select>` (naturally single) |
| Multi-pick cards | Multiple checkboxes | Multi-select `<select multiple>` or stacked dropdowns |
| Card layout | CSS Grid auto-fit 280px | Single column, full width |
| Card collapse | Always open | Collapsible accordion — tap header to expand |
| Lock button | Top right of card header | Same — full width on mobile, larger tap target |
| Output box | Resizable textarea | Fixed height textarea, scroll inside |
| Buttons | Inline flex row | Full width stacked or 2-per-row |
| History panel | Collapsible below output | Same, full width |

### Dropdown Behavior Rules
- singlePick cards → standard `<select>` (one choice enforced by browser)
- Multi-pick cards → `<select multiple size="4">` or a scrollable tag-style picker
- Default option on each: `"— select —"` (value = `""`, excluded from prompt)
- Multi-select hint text: `"Hold Ctrl / tap multiple to select"`
- Selected count badge on collapsed card header: e.g. `Personality (2)`

---

## 8. PROMPT BUILDER — NO CHANGES NEEDED

The `generatePrompt()` logic is identical in v2. Only the **data collection** changes:

**v1 collection:**
```javascript
document.querySelectorAll('.trait-checkbox:checked').forEach(cb => {
    result[cb.dataset.key].push(cb.value);
});
```

**v2 collection (dropdowns):**
```javascript
document.querySelectorAll('select.trait-select').forEach(sel => {
    Array.from(sel.selectedOptions)
        .filter(opt => opt.value !== "")
        .forEach(opt => result[sel.dataset.key].push(opt.value));
});
```

Everything else — S1 through S8 sentence assembly, article grammar, singlePick guard, style tail fallback — is copy-paste identical.

---

## 9. NEW CHAT HANDOFF PROMPT

Paste this verbatim to start the new chat:

---

> I'm building a mobile-first dark neon version of my GnomeLife Character Prompt Generator. I have a complete blueprint .md with all trait data, pipeline structure, prompt logic, and design specs. The aesthetic is **Shared Frequency** — Gothic-Roman cinematic dark neon: teal (#00e5ff), cyan (#00bcd4), magenta (#e040fb) on deep charcoal (#0a0a0f). 
>
> Key changes from the desktop version:
> - **Dropdowns** instead of checkbox grids (single `<select>` for singlePick cards, `<select multiple>` for multi-pick)
> - **Collapsible accordion cards** — tap header to expand/collapse, shows selected count badge when collapsed
> - **Mobile viewport** — 375–430px, single column layout, large tap targets
> - **Same Lock/Unlock, Clear All, Random, and History panel logic** — just reskinned
> - **Google Fonts**: Cinzel for headers, Inter for body
> - Card hover/locked glow effects using box-shadow
>
> I'm uploading the blueprint .md now. Please read it fully before writing any code, then build the complete single-file HTML.

---

## 10. BUILD CHECKLIST FOR NEW CHAT

- [ ] Paste handoff prompt above
- [ ] Upload `GnomeLife_CharacterGen_Blueprint.md`  
- [ ] Upload `Character_Generator.html` (v1) as reference
- [ ] Confirm Claude reads both files before starting
- [ ] Request single-file HTML output
- [ ] Test: Random on locked card — selections unchanged ✓
- [ ] Test: Clear All on locked card — selections unchanged ✓
- [ ] Test: Gnome selected → no "looms in distance" sentence ✓
- [ ] Test: Empty renderstyle → fallback style tail fires ✓
- [ ] Test: "an adventurous gnome" not "a adventurous gnome" ✓
- [ ] Test: History saves, restores, deletes correctly ✓
- [ ] Deploy to Firebase or Netlify under Shared Frequency brand

---

*Blueprint authored: 2026-05-27 | Wilad AI System — Claude Architecture Agent*
