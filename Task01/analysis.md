# TASK 1 – Problem Analysis and Data Identification

### 1. Justified System Data Inventory
* **household_number:** Stored as `unsigned int` to support district scale (800,000 houses).
* **category:** Stored as a single `char` flag for discrete classification codes.
* **previous_reading / current_reading:** Stored as `unsigned short` to match physical 16-bit utility meter loops.
* **units_consumed:** Stored as `unsigned int` to hold cumulative calculation deltas.
* **fixed_charge / energy_charge / total_bill:** Stored as `long` in whole Indian Paise to prevent rounding precision drift.

### 2. Operational Rules
* **Non-Negativity Rule:** Total Bill >= Fixed Charge.
* **Conservation of Value:** Total Bill = Fixed Charge + Energy Charge.

### 3. Alternative Concept Analysis
If stored as text strings (e.g., "01530"), checking and converting data requires O(d) linear digit parsing time and consumes 6 bytes of space instead of 2 bytes, causing a 200% memory overhead at scale.
