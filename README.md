# Race driver: Grid, Real drivers and teams mod

A mod for **Race Driver: GRID** (Codemasters, 2008) that replaces the game's
fictional AI drivers and teams with real drivers and teams that were active around 2006/2007. 

---

## 📑 Overview

GRID mixes a handful of real drivers (Kristensen, Pirro, the Müller brothers,
the Corvette and Aston Martin works drivers, ...) with hundreds of made-up
ones. This mod replaces the made-up ones, discipline by discipline, with
drivers who were actually racing in that series around 2007 (the full list is
in [`changes.csv`](changes.csv)):

* **Open wheel** — F1 stars at the top, then GP2, A1GP, F3 and junior-formula drivers.
* **Touring cars** — WTCC, BTCC and DTM drivers.
* **Stock cars** — NASCAR Busch, Truck and ARCA drivers.
* **GT1 / GT2 / Prestige / Club GT** — FIA GT, ALMS, Le Mans, British GT and Porsche Cup drivers.
* **Prototypes** — Le Mans, ALMS and Grand-Am drivers.
* **Pro Muscle** — V8 Supercars and US GT/Trans-Am drivers.
* **Pro Tuned** — Super GT and Super Taikyu drivers.
* **Drift** — D1 Grand Prix and Formula Drift drivers.

Names are matched to the career level where you first meet each driver, so
reputations grow as you progress:

* **Global** — the stars of 2007: Räikkönen, Alonso and Hamilton in open
  wheel, Priaulx, Ekström and Schneider in touring cars, Whincup and Lowndes
  in V8 Supercars, and the top D1 and Formula Drift names.
* **Expert** — well-known names such as Sebastian Vettel, Juan Pablo Montoya
  and Sébastien Bourdais.
* **Pro** and **Rookie** — second-tier drivers and the prospects of 2007.
  Where these levels have fast AI slots, they are filled by drivers who were
  still lesser known then but became big names later, like Hülkenberg,
  Grosjean, Pérez, Ricciardo and Bottas.

Each driver keeps the skill rating, team and events of the slot they replace,
so the game's balance is unchanged. Nationalities are updated to match. The
level of every driver is listed in [`changes.csv`](changes.csv).

The final boss, **Ravenwest**, is driven by **Michael Schumacher** and
**Allan McNish**.

In total the mod changes:

* **613 drivers** renamed, with matching nationalities.
* **12 real GT drivers** whose names had been altered by the developers restored
  (e.g. "Peter Kovac" → Peter Kox, "Vincent Schifo" → Vincent Vosse).
* **185 teams** renamed to real teams from the same series, chosen to fit their
  drivers' ratings (e.g. ART Grand Prix, iSport International, Triple Eight).
  Open-wheel teams use GP2 and F3 team names, as F3 is the top open-wheel
  series in the game.
* **180 car liveries** renamed, so the team names in the team-selection menu
  match too.

Real drivers and teams already in the game are left untouched, and the
**Ravenwest** and **Lumenition** team names are kept. Car
liveries themselves (the paint jobs) are unchanged.

The mod works in every language the game supports: English, US English,
French, German, Italian and Spanish.

---

## 📁 Project structure

The repository mirrors the layout of the GRID installation folder, so the
folders can be copied straight into the game.

* **database/**
  * **`database.bin`** — the game database: driver names, nationalities and
    skill ratings.
* **language/**
  * **`language_eng.lng`** — English text: driver, team and livery names.
  * **`language_use.lng`** — US English.
  * **`language_fre.lng`** — French.
  * **`language_ger.lng`** — German.
  * **`language_ita.lng`** — Italian.
  * **`language_spa.lng`** — Spanish.
* **changes.csv** — the full list of renamed drivers: database id, discipline,
  career level, skill rating, original name, new name, nationality and team. Not needed to
  install the mod, just a reference.

The DLC language files (`language_xxx_dlc_0.lng`) are not part of the mod, so
your own copies stay in place.

---

## 🔧 Installation

### Prerequisites

The mod was made for the **Steam version** of Race Driver: GRID, but should work for other versions as well.

### Installing

1. **Find your GRID installation folder:**

   In Steam, right-click **Race Driver: GRID** → **Manage** → **Browse local
   files**. By default this is something like:

   ```
   C:\Program Files (x86)\Steam\steamapps\common\Grid
   ```

2. **Back up the originals:**

   Copy the game's `database` and `language` folders somewhere safe. This is
   optional (see [Uninstalling](#-uninstalling)), but it makes switching back
   quicker.

3. **Copy the mod files into the game:**

   Download this repository (green **Code** button → **Download ZIP**, or
   `git clone`), then drag its `database` and `language` folders into the GRID
   installation folder. When Windows asks, choose **Replace the files in the
   destination**.

---

## 🗑️ Uninstalling

Either copy your backed-up `database` and `language` folders back into the
GRID installation folder, or let Steam restore the original files:
right-click **Race Driver: GRID** → **Properties** → **Installed Files** →
**Verify integrity of game files**.

---

## ⚙️ How it was made

The files were edited with the community **Ego Database Editor** and **Ego
Language Editor**, which export GRID's `database.bin` and `.lng` files to XML
and back.

* **Driver names** are not stored in the database itself. Each driver points to
  a first-name and a surname entry in the language files (`db_<key>`). Many
  fictional drivers shared entries (several drivers used the same "John"), so
  every renamed driver got its own new entries (`db_rn<id>a` / `db_rn<id>b`)
  and the database now points to those.
* **Team names** are edited in place in the language files; the database only
  references them by key.
* **Team-selection menu names** come from the car *liveries*, not the teams —
  each livery in the database's `vehicle_livery` table has its own name entry,
  which was renamed to match its team.
* All changes were applied to every language file, so the names are the same
  whatever language the game runs in.
