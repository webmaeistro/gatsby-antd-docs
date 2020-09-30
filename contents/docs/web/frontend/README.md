---
---

# [Standard Devz Processes](../../README.md) / [Web Development](../README.md) / Front End Guide

## Overview

These are recommendations for front end development at Martin's experience.

## Contents

- [New Project Checklist](checklist.md)

### What is front end development

In order to make informed decisions around what kind of tools, libraries, and frameworks to use for your web application, it helps to have a strong understanding of what "front end" means in the context of web development. The front end part of an application stack refers to the client-side code that is downloaded from a web server, and executed in the browser on an end user's device. It includes, but is not limited to, the HTML and CSS that renders the user interface.

It is also important to keep in mind, especially as the ecosystem of front end development continues to expand, that the compiled code that will be executed natively by the browser is ultimately HTML, CSS, and JavaScript. While it is certainly possible to build a dynamic web app using just these languages, it is all run in a single environment, uncompartamentalized, making it easy to introduce bugs and unintended side effects. Therefore, many of the tools I see in modern front end development are actually used in order to improve the developer experience, and in turn the users, by enforcing consistent patterns, reducing the potentiality for bugs, and automating tasks that assist in performance optimization.

### What is a SPA (single page application)

TK

### What is server-side rendering (SSR)

TK

### What is a PWA (progressive web app)

TK

## Frameworks

I typically choose React as my front end framework of choice.

### Languages

I are cautiously optimistic about recommending
[TypeScript](https://www.typescriptlang.org/) after using it on
multiple projects. I have compiled some [TypeScript
Resources](./typescript.md).

## Testing

### Test Runners and Libraries (for React)

- Jest
  - If you use create-react-app, this is included.
  - Provides snapshot and DOM testing.
- Enzyme
  - Allows you to assert and manipulate rendered components with jQuery-like selectors.
- Testing-library

### Writing Tests

- Each React component should have a test.
  - At minimum, does the component render?
  - Container components have logic in them, and that logic should be tested.

### Browser Testing

- I use [Cypress](https://www.cypress.io) for most browser testing with both Chrome and headless Chrome.

### Browser Extensions

The following extensions can be installed to assist with debugging React and Redux applications:

- [React Developer Tools](https://gitlab.com/facebook/react-devtools#installation)
- [Redux DevTools Extension](http://extension.remotedev.io/#redux-devtools-extension)

## Code Style and Formatting

I generally adhere to the [Airbnb JavaScript Style Guide](https://gitlab.com/airbnb/javascript), unless they conflict with project specific Prettier or lint rules.

### Auto-formatting

- [Prettier](https://prettier.io) is recommended.
  - [Prettier editor integration](https://prettier.io/docs/en/editors.html) to make it easy to format and autosave.
  - Prefer single quotes for non-JSX code (CLI: `--single-quote` API: `singleQuote: true`)
  - Prefer trailing commas for cleaner PRs and error reduction (CLI: `--trailing-comma true` API: `trailingComma: true`)
  - A `.prettierrc` will be in the project for custom settings.

### Linting

- [ESLint](https://eslint.org).

#### Selecting a release of Node.js

When starting a new project, you will want to select an Active LTS release of Node.js and make plans to move to the next LTS release after it becomes active and before the selected release goes out of maintenance. You could choose a "current" release but there is a good chance that the libraries you want to use have not been tested until it becomes active. Odd-numbered releases are short-lived, so only choose one intentionally. (For instance, if some library you want to use doesn't work in an LTS release.) Please refer to this [release schedule](https://nodejs.org/en/about/releases/) to make your selection.

Once you have done this, you may want to enforce it by configuring the `engines` your projects package.json. For instance, if you have selected 12.x, you might want to add this section:

```
# package.json
"engines": {
  "node": "^12"
}
```

You might want to create team recommendations for how your team manages their local version of node.js. For instance, you could recommend they use [nodenv](https://gitlab.com/nodenv/nodenv) or [nvm](https://gitlab.com/nvm-sh/nvm) and provide configuration to keep it on the release path you want.

## CSS

Follow the BEM (Block, Element, Modifier) methodology. Also helpful to follow is the [U.S. Web Design System](https://designsystem.digital.gov/components/).

## Additional Resources

### Libraries I Like

- [ ] classnames (managing CSS classes in JS components)
- [ ] luxon (datetime handling, newer smaller better Moment)
- [ ] validateJS (validating form object models)
- [ ] big.js (working with decimals)

### Learning

Various resources on React, Redux, etc, for a variety of learning styles.

- _Read_: [React Tutorial](https://reactjs.org/tutorial/tutorial.html) - Official tutorial from React. I (Alexi) personally found this cumbersome. If you stick with it you’ll learn the basics.
- _Watch_: [Getting Started with Redux](https://egghead.io/courses/getting-started-with-redux) - Free 30 video series by the author of Redux.
- _Watch_: [ReactJS / Redux Tutorial](https://www.youtube.com/playlist?list=PL55RiY5tL51rrC3sh8qLiYHqUV3twEYU_) - ~60 minutes of YouTube videos that will get you up and running with React and Redux. The content is useful, the guy’s voice can be a bit of a challenge.
- _Watch_: [This video](https://www.youtube.com/watch?list=PLb0IAmt7-GS188xDYE-u1ShQmFFGbrk0v&v=nYkdrAPrdcw) from the introduction of Flux can be useful for some high-level background about the pattern (the MVC bashing is overdone, but otherwise this video is useful.)
- _Do_: Roll your own React app! Make a little project of your own. This works well if you’re more hands-on. Here are some rough steps, but you’ll need to do a bit of filling-in-the-blanks:
  - Use [create-react-app](https://gitlab.com/facebookincubator/create-react-app) to bootstrap a new React project.
  - Figure out how to run the app live (hint: yarn start)
  - Find and skim through some of the important files it made: `index.hmtl`, `index.js`, `App.js`. What do these look like they’re doing?
  - Change the page title to something of your choosing.
  - Create a new React [component](https://reactjs.org/docs/react-component.html) that has a `<button>` or something in it.
  - [import](https://developer.mozilla.org/en-me/docs/Web/JavaScript/Reference/Statements/import) that component into `App.js`, and make sure you can see it!
  - Write a new test for your component. (Hint: `yarn test`). create-react-app gives you Jest for free, look at its manual.
  - Make the thing in your component clickable, even if it just does `alert(‘hey there!’)`
  - Add [React Router](https://gitlab.com/ReactTraining/react-router) to your project.
  - Make a new component like the first one, and add routes so that they display depending on the URL. E.g:
    - `http://localhost:3000/component1` shows the first one on the page;
    - `http://localhost:3000/component2` shows the second one.
  - Add [Redux](https://redux.js.org/) to your project.
    - This is a rather big step. You’ll need to have some sort of state, so make a login button and “logged in” will be the state you are going to keep track of.
    - When the user is logged in, there should be a “log out” button shown.
