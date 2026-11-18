# Playwright To-do App Automation (TypeScript)

Practice project: end-to-end tests for the TodoMVC demo app
https://todomvc.com/examples/react/dist/

I built this while following the tutorial "Playwright MiniProject: End-to-End Automation
with the To-do App" by Raghav Pal (AutomationStepByStep). The test scenario is my own
version, and I added my own checks.

## What is tested
- Add 5 to-do items (Exercise, BreakFast, Go to School, Lunch, Study)
- Mark all items as complete, then un-mark them one by one
- Complete three items and check the Active view shows only the two that are left
- Check the item counts and that "Lunch" is still visible in the All view

## Tech
Playwright, TypeScript, Node.js, VS Code

## Features I practised
- Locators (test id, role, text) and assertions
- Tag a test with `@sanity` and run only tagged tests
- HTML report, screenshot on failure, video on failure and trace on failure
- Headed mode, slow motion (`slowMo`), UI mode and the debug inspector

## How to run
Install Node.js (LTS), then:

    npm install
    npx playwright install
    npx playwright test --headed --project=chromium --grep "@sanity"
    npx playwright show-report

## Project structure
- `tests/todo.spec.ts` the test
- `playwright.config.ts` browser, screenshot, video and trace settings
- `docs/screenshots/` report, failure and trace screenshots

## Screenshots

Passing run in the HTML report:

<img width="1535" height="808" alt="passed-report png" src="https://github.com/user-attachments/assets/678c24be-028f-4ebd-a6ea-5d4e919680e6" />

A deliberate failing check (expected 3 items, got 2) to see how failures look in the report:

<img width="1535" height="812" alt="failed-assertion png" src="https://github.com/user-attachments/assets/82f90a5f-3867-4018-b83f-6283f0eadf34" />


Screenshot captured automatically on failure:

<img width="1517" height="813" alt="failure-screenshot png" src="https://github.com/user-attachments/assets/5a3582db-2304-41be-b316-05672077fdec" />


Trace viewer showing each step:

<img width="1531" height="813" alt="trace-viewer png" src="https://github.com/user-attachments/assets/8eb81726-2585-4163-b2ac-5cf5d3505b91" />


## What I learned
- A locator is how Playwright finds an element, and an assertion decides whether the test passes.
- A "strict mode violation" means a locator matched more than one element. I fixed it by
  narrowing the locator to one to-do item.
- A test needs `page.goto()` first, or it waits on a blank page and times out.
- Reading the HTML report, the failure screenshot and the trace shows exactly which step failed and why.
- A PowerShell quirk: tags like `@sanity` must be in quotes.

