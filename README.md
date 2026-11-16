# SpendWise

SpendWise is a simple personal budget tracker. Set a monthly budget, add expenses with a name, category, amount, and date, and see your spending total, remaining balance, and budget progress update immediately. You can also remove an expense.

## Run the project

Open `index.html` in a modern web browser. No installation or build step is required. The app uses USD for its displayed amounts.

Expense and budget data are kept in the current page session; refreshing the page starts a new session. The app does not send data to a server.

## JavaScript concepts

- **Variables and data types:** `monthlyBudget` is a number that can change; `expenses` is an array of expense objects; `const` is used for references that do not need reassignment.
- **User input and events:** HTML forms collect the budget and expense details. JavaScript listens for form submissions and remove-button clicks instead of using blocking `prompt()` dialogs.
- **Type conversion and validation:** Numeric input strings are converted with `Number()`. The app checks that amounts are finite and greater than zero, and trims expense names before adding them.
- **Arrays and objects:** Each expense is an object containing a name, amount, category, and date. The array stores all expenses for the current page session.
- **Arithmetic:** The app adds expense amounts, subtracts total spending from the budget, and calculates the percentage of the budget spent.
- **DOM updates:** JavaScript updates the summary, progress bar, and expense list in the page. Expense text is added with `textContent` so user-entered names are displayed as text.

## How variables are used

`monthlyBudget` holds the user's current monthly budget. `expenses` stores the expense objects. Each form field is referenced by a `const` variable so event handlers can read the user's input. The total and remaining balance are calculated from the current values rather than kept as duplicate state.

## How user input is collected

The budget form accepts a positive monthly amount. The expense form collects a description, positive amount, category, and date. The browser's number, date, and required-field controls provide basic validation; JavaScript performs additional checks before changing the app data.

## How calculations are performed

- **Total spent:** Adds the `amount` of every expense with `reduce()`.
- **Available to spend:** Subtracts total spending from the monthly budget.
- **Budget used:** Divides total spending by the budget and multiplies by 100. If no budget has been entered, the percentage is zero.
- **Progress bar:** Shows the budget percentage, with the visual bar capped at 100%. The displayed percentage can exceed 100% to show overspending.

## How functions organize the code

- `formatCurrency()` and `formatExpenseDate()` format values for display.
- `getTotalExpenses()`, `calculateRemainingBalance()`, and `calculateSpendingPercentage()` perform the budget calculations.
- `updateDashboard()` refreshes the summary and progress indicator.
- `createExpenseElement()` and `renderExpenses()` build and display the expense list.
- `initializeApp()` sets the current month and today's date when the page loads.
- Form event handlers validate user input, update the data, and refresh the interface.