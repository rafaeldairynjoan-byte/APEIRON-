# Apeiron

One page, two features, switched with the tabs at the top:

1. **Land Calculators** with two calculators inside: Acres and Small Lot.
2. **Timesheet** for agents, with 2-week pay periods and CSV export.

No build step, no dependencies. It is one static `index.html`. Link straight to a view with `#acres`, `#small` or `#timesheet` at the end of the page address.

## Land Calculators

- **Acres Calculator**: target property plus 5 sold comps, average price per acre, buyer value and offer ladder, flood zone questions, and a builder method.
- **Small Lot Calculator**: inputs, discounts and offer ladder, with 3 sold comps at the bottom.

Nothing you type into the calculators is saved or sent anywhere.

## Timesheet

Click **Timesheet** at the top of the page, or link straight to it with `#timesheet`. (The old `timesheet.html` just redirects there.)

- Sample agents and times are loaded the first time you open it. Use **Reset sample data** to reload them, or **Remove selected** and **Add** to manage your own agents.
- Use **Log in**, **Bio out**, **Bio in**, **Lunch out**, **Lunch in** and **Log out** to stamp the current time on today's row. Any time can be corrected in the table.
- Pay periods are 14 days. Use Previous / Next, or type any start date in **2 weeks starting**. **Pay schedule starts** sets where "Current" snaps to.
- Hours = log out minus log in. Nothing is deducted for lunch or bio breaks (they are still recorded and exported).
- Totals: Day, 2 weeks and Month, each with an editable date, for the selected agent and for all agents in one table with a grand total.
- **Export CSV (this agent)** and **Export CSV (all agents)** download the 14-day pay period with H:MM and decimal hours and a TOTAL row per agent.
- Data is saved in the browser (localStorage), so it stays on that device and browser.

## Each comp records

Property address, date of purchase, purchase price, lot size (sq ft), sold by, and bought by. Acres comps also have an optional acres override.

## Export comps

Each comps card has two buttons:

- **Export CSV** downloads the filled-in comps (with price per sq ft, price per acre and the average) as a spreadsheet file.
- **Copy** puts the same table on your clipboard to paste into Excel or Google Sheets.

Empty comps are left out. Exporting works once the page is hosted (for example on GitHub Pages) or opened from your computer.

## Acres Calculator math

- Acres = square feet / 43,560 (or the acres override, if you type one)
- Comp price per acre = purchase price / acres
- Average price per acre = mean of the comps that have a price and a size (empty comps are skipped)
- Target value to sell = target acres x average price per acre
- Last resort MAO = value less 20%
- MAO of land = value less 30%
- First offer = 50% of value
- Start your range = 25% of value (first offer / 2)
- Builder method: land price = 15% of ARV, then the same offer ladder

## Small Lot Calculator math

- Average purchase price = mean of the comp purchase prices (or the override, if you type one)
- 30% and 20% = those percentages of the average
- Last resort MAO = average less 20%
- MAO of land = average less 30%
- First offer = 50% of the average
- Start of your range = 50% of the land appraised value

To change any percentage, edit `offers()`, `calcAcres()` or `calcSmall()` in `index.html`.

## Publish with GitHub Pages

1. Upload these files to a new **public** GitHub repository, with `index.html` at the top level (keep `timesheet.html`, it redirects old links).
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then branch **main** and folder **/ (root)**, and click **Save**.
4. After a minute or two, your site is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

Every commit to `main` updates the site automatically.
