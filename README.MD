# React Practical Exams

## About the Project

This project contains six practical exams that I worked on using React and Vite. Each exam helped me practice different React concepts, such as `useState`, `useEffect`, `useRef`, Context, `useMemo`, `useCallback`, and `useReducer`. While coding, I also encountered some problems that I had to fix and test to make sure the applications worked properly.

## Exam 1 — Smart Task Counter

### Completed Requirements
- Used `useState` to keep track of the count and target.
- Added Increment, Decrement, Plus Two, and Reset buttons.
- Displayed the status based on the current count.
- Used two functional state updates for the Plus Two button.
- Made sure the count cannot go below zero.
- Disabled Increment and Plus Two when the target is reached.

### Known Limitations
- The target is fixed at 5.
- The application only counts tasks and does not save them.

### How I Tested It
1. Checked if the count starts at 0 and the target is 5.
2. Tried all four buttons.
3. Checked if the count stays at zero when I keep clicking Decrement.
4. Checked if the status changes when the count increases.
5. Tested the disabled buttons after reaching the target.
6. Clicked Reset to check if the count returns to zero.

### Problem I Encountered
At first, using `setCount(count + 1)` twice did not increase the count by two because both updates used the same count value. I changed it to `setCount(c => c + 1)` twice so React could process both updates correctly.

## Exam 2 — Live Search and Timer

### Completed Requirements
- Used `useState` to store the search query, visible users, and timer.
- Used `useEffect` to run the search after a 300-millisecond delay.
- Used `setTimeout` and `clearTimeout` to manage the search delay.
- Added a timer that increases every second.
- Used `clearInterval` to clean up the timer.
- Updated the browser tab title based on the number of users found.
- Used a functional state update for the timer.

### Known Limitations
- The search only checks the users' names, not their roles.
- The application uses sample data instead of fetching users from an API.
- The timer starts at zero again when the page reloads.

### How I Tested It
1. Searched for different user names and checked the results.
2. Typed quickly to check if previous pending searches were canceled.
3. Checked if the timer continued increasing every second.
4. Searched while the timer was running.
5. Checked if the browser tab title changed when the number of results changed.

### Problem I Encountered
The timer could get stuck at one when I used `setSeconds(seconds + 1)` inside an interval that was created only once. I fixed it by using `setSeconds(s => s + 1)` so the timer could use the latest state value.

## Exam 3 — Accessible Form Toolkit

### Completed Requirements
- Used `useState` to manage the name, email, password, errors, and success message.
- Added validation for required fields, email format, and password length.
- Displayed error messages when the inputs were invalid.
- Used `useRef` to focus on the first invalid field.
- Used `useRef` to remember the previous successfully submitted email.
- Practiced fixing a counter that used a ref instead of state.

### Known Limitations
- The form is only a front-end demonstration and does not save registration details to a database.
- The email validation checks the basic format only.

### How I Tested It
1. Submitted the form without entering anything.
2. Tried an invalid email and a password shorter than eight characters.
3. Checked if the first invalid input received focus.
4. Submitted valid information and checked the success message.
5. Submitted another valid email and checked if the previous email was displayed.

### Problem I Encountered
I learned that changing `ref.current` does not automatically update the interface because it does not trigger a re-render. For a counter that needs to update on the screen, I used `useState` and its setter function instead.

## Exam 4 — Application Preferences

### Completed Requirements
- Created a Preferences Context using `createContext`.
- Used `useState` to manage the theme and font size.
- Added a button to switch between light and dark themes.
- Added Small (14px), Medium (16px), and Large (18px) font-size options.
- Used `useContext` to access the preferences in different components.
- Created a custom `usePreferences` hook.
- Added an error if the hook is used outside `PreferencesProvider`.

### Known Limitations
- The theme and font size return to their default values when the page reloads.
- The preferences are not saved in browser storage or a database.

### How I Tested It
1. Switched between the light and dark themes.
2. Selected each font-size option.
3. Checked if the Article Preview changed based on the selected preferences.
4. Checked the browser console for errors.

### Problem I Encountered
The default Vite page appeared instead of my preferences dashboard. I fixed this by updating `App.jsx` to display `PreferencesProvider` and `Dashboard`. I also checked that `main.jsx` imported the correct `App.jsx` file.

## Exam 5 — Product Explorer

### Completed Requirements
- Generated 500 sample products.
- Added a search field and category filter.
- Added sorting by name, price, and rating.
- Used `useMemo` to avoid recalculating filtered and sorted products when the dependencies have not changed.
- Used `useCallback` to memoize the product selection function.
- Used `React.memo` for the product components.
- Added a View Product button for each product.

### Known Limitations
- The product data is generated locally and is not saved in a database.
- Clicking View Product displays an alert instead of opening a separate product details page.

### How I Tested It
1. Checked if all 500 products appeared.
2. Searched for products by name.
3. Tried the available category filters.
4. Sorted the products by name, price, and rating.
5. Clicked View Product to check the selected product name.
6. Changed the counter and checked the console to observe component rendering.

### Problem I Encountered
Filtering and sorting can run again whenever a component renders. I used `useMemo` with `search`, `category`, and `sort` as dependencies so the results can be reused when those values have not changed. I also used `useCallback` and `React.memo` to help avoid unnecessary child component renders when their props stay the same.

## Exam 6 — Issue Tracker State Engine

### Completed Requirements
- Used `useReducer` to manage the issues.
- Created a separate reducer for adding, completing, reopening, deleting, and clearing completed issues.
- Used immutable state updates.
- Created a custom `usePersistentReducer` hook.
- Used `localStorage` to save and load issues.
- Added All, Open, and Done filters.
- Added basic reducer checks for adding, completing, and deleting issues.

### Known Limitations
- Issues are saved in the current browser's local storage instead of a database.
- The reducer checks are simple console-based checks, not a complete automated testing setup.
- Two issues created within the same millisecond could receive the same ID.

### How I Tested It
1. Added a new issue.
2. Completed an issue and reopened it.
3. Tried the All, Open, and Done filters.
4. Deleted an issue.
5. Cleared the completed issues.
6. Refreshed the page to check if the issues were still saved.
7. Ran the reducer checks and checked the browser console.

### Problem I Encountered
I learned that directly modifying the existing state can cause problems with React updates. To avoid this, my reducer returns new objects and arrays using spread syntax, `map()`, and `filter()` instead of directly modifying the existing state.

## How to Run the Project

1. Open the project folder in VS Code.
2. Open the terminal in the project directory.
3. Install the dependencies by running:

   `npm install`

4. Start the development server:

   `npm run dev`

5. Open the local URL shown in the terminal.

## GitHub Repository

**Repository Link:** Add my GitHub repository URL here if Git is required.

## Conclusion

Working on these six practical exams helped me practice the different React concepts and understand how they work in actual applications. I also learned how to fix problems with state updates, timers, component rendering, form validation, and data persistence. Each exam gave me more practice in writing code, testing the results, and correcting errors along the way.
