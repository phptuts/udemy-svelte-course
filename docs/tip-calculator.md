# Tip Calculator

In this project we'll be building a tip calculator. By the end of this project you should be able to:

## Demo

[Tip Calculator](https://phptuts.github.io/udemy-svelte-tip-calculator/)

## Learning objectives

- import css packages from node_modules folder
- toggle classes dynamically on html elements based on conditions
- create button click events
- create reactive variables


## 1) Pre Setup

In this section we go over everything you will need to get started with building svelte projects.

### Resources

- [Visual Code](https://code.visualstudio.com)
- [Visual Code Svelte Extension](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)
- [Node Js](https://nodejs.org)

### Steps

Let's get started.  Links to the code and notes in the resources.  In this series I am going to be using visual studio code as my code editor.  You can download it at https://code.visualstudio.com.  

You will also need to download and install the svelte extension for visual studio code.  Click on the extension button and type in svelte.  It should be the first one that comes up.   

You will also need to install nodejs.  Go to nodejs.org and download & install the latest version.

## 2) Svelte Setup

How to install svelte js on your laptop or computer.

### Resources

- [Code](https://github.com/phptuts/udemy-svelte-tip-calculator/tree/video-2-project-setup)
- [Svelte Website](https://svelte.dev/)

### Steps

1) Open visual studio code to the project folder you are going to use for your tip calculator.

2) Open a terminal on visual studio code 


3) Type in npx degit command to clone the sveltes/template repo into your project folder 

```bash
npx degit sveltejs/template .
```

4) Type in npm install to install the dependencies
```bash
npm install 
```

5) Then type in npm run dev to start the website

```bash
npm run dev
```

6) Go to your local website, [localhost:5000](http://localhost:5000) and make sure that svelte is running.

## 3) Svelte Overview

### Package.json
1. Open the package.json file.  

2. Notice that svelte is a dev dependency.  This means that the whole svelte library does not ship with your app.  Svelte will only include the parts of it's library you need when compiling your application.

3. Also note that the three commands in your package.json, dev, build, and start.

  - Start will serve the index.html file in the public folder
  - Dev will serve the index.html file in the public folder and will recompile your application when it changes.  This is because we are passing -w which means watch.
  - Build is for building your app for production.
 

```json
"scripts": {
    "build": "rollup -c",
    "dev": "rollup -c -w",
    "start": "sirv public"
  },
```

### Rollup

Open up the rollup.config.js file.  This is where svelte gets compiled. The starting point for your svelte app is src/main.js.  Your app javascript will be compile into a file called bundle.js and your css will be compiled into a file called bundle.css.

### Scripts Folder

It has one script for turning your project into a typescript project.

### Src Folder

Open up source folder and you will see the main.js file.  This is the entry point in your application.  The App component is being passed a prop named "name".  Go ahead change the prop store your name as it's value.  This will changes page to Hello {YourName}.  Look at the target being passed into the App component.  In the App Component we are targeting the body element.  This means that the App.svelte component will control the body of the page.

Open the App.svelte file.  It's taking in prop name and showing that on the page.  This is why the page now says Hello {Yourname}.  Note all components will go into the src folder.

### Public Folder

Open up the public folder.  Here you will find the index.html, global.css files and the build folder we talked about previously. The global.css is just a css file no magic there.  Same for our index.html.  These files already have link and script tags for the bundle.js and bundle.css files.


## 4) Svelte Cleanup / Install Package

- We get milligram css working with our svelte website
- Cleanup all the added html and css code

### Resources

- [Code](https://github.com/phptuts/udemy-svelte-tip-calculator/tree/video-4-cleanup-install-packages)
- [Rollup Plugin Css Only](https://github.com/thgh/rollup-plugin-css-only)
- [Milligram CSS](https://milligram.io/)
- [Gh Pages](https://github.com/tschaub/gh-pages)

### Steps

1) Install packages

```bash
npm install milligram gh-pages rollup-plugin-css-only --save-dev
```

2) Import the rollup plugin into our rollup config file.

```javascript
import css from 'rollup-plugin-css-only';
```

3) Add the rollup plugin to the list of plugins 

```javascript
css({ output: 'public/extra.css'})
```

4) Import milligram css into our main.js file.

```javascript
import 'milligram/dist/millgram.min.css'
```

5) Remove the prop being inserted into our app component.

```javascript
const app = new App({
	target: document.body,
});
```

6) Delete everything inside our App.svelte file.

7) Delete everything inside our global css file

8) Install the Roboto font

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
body {
  font-family: 'Roboto', sans-serif;
}
```

9) Change the title to Tip Calculator in the index.html file.

```html
<title>Tip Calculator</title>
```

10) Make all the links relative for github pages.

11) Insert a link css tag for our extra css file which will contian our milligram.css

```html
<link rel='stylesheet' href='extra.css'>
```

12) Test Everything out by running npm run dev

13) Inspect element and make sure there are no 404s.

## 5) HTML For Tip Calculator

We build out our html and css in this section.

### Resources
- [Code](https://github.com/phptuts/udemy-svelte-tip-calculator/tree/video-5-html)
- [Emmet Cheat Cheat](https://docs.emmet.io/cheat-sheet/)
- [Milligram CSS](https://milligram.io/)


### Steps

1) Add the container section

```html
<main class="container">

</main>
```

2) The title to the page

```html
<main class="container">
  <section class="row">
        <div class="column">
            <h1>Tip Calculator</h1>
        </div>
    </section>
</main>
```

3) Add a style tag and center the h1 tag.

```html
<style>
  h1 {
    text-align: center;
  }
</style>
```

4) Add another for the price input

```html
  <section class="row">
    <div class="column">
      <label for="price">Price</label>
      <input type="number" id="price" />
    </div>
  </section>
```

5) Add the input for the tip 

```html
<section class="row">
    <div class="column">
      <label for="tip">Tip (15%)</label>
      <input type="range" min="0" max="100" id="tip" />
    </div>
  </section>
```

6) Make a style to make the range input take up 100% of width

```css
#tip {
    width: 100%;
}
```

7) Create a section with 3 buttons for preset tips.

```html
<section class="row">
    <div class="column"><button class="button button-outline">15%</button></div>
    <div class="column"><button class="button button-outline">25%</button></div>
    <div class="column"><button class="button button-outline">30%</button></div>
  </section>
```

8) Make the button take 100% of the width


```css
button {
    width: 100%;
}
```

9) Create the total tip at the button of the page

```html
<section class="row">
    <div class="column">
      <h2>Total Tip $12.12</h2>
    </div>
  </section>
```

10) Style the calculated Tip to be center and increase the top margin

```css
h2 {
    text-align: center;
    margin-top: 20px;
}
```

### Final Code 

```html
<style>
    h1 {
        text-align: center;
    }
    h2 {
        text-align: center;
        margin-top: 20px;
    }
    #tip {
        width: 100%;
    }
    button {
        width: 100%;
    }
</style>
<main class="container">
    <section class="row">
        <div class="column">
            <h1>Tip Calculator</h1>
        </div>
    </section>
    <section class="row">
        <div class="column">
            <label for="price">Price</label>
            <input type="number" id="price">
        </div>
    </section>
    <section class="row">
        <div class="column">
            <label for="tip">Tip (15%)</label>
            <input type="range" min="0" max="100" step="1" id="tip">
        </div>
    </section>
    <section class="row">
        <div class="column">
            <button class="button button-outline">
                15%
            </button>
        </div>
        <div class="column">
            <button class="button button-outline">
                25%
            </button>
        </div>
        <div class="column">
            <button class="button button-outline">
                30%
            </button>
        </div>
    </section>
    <section class="row">
        <div class="column">
            <h2>Calculator Tip: $12.00</h2>
        </div>
    </section>
</main>

```

## 6) Binding Variables and Class

- How to connect variables to inputs
- How to toggle classes based on conditions
- How to create click events with buttons

### Resources

- [Code](https://github.com/phptuts/udemy-svelte-tip-calculator/tree/video-6-binding-variables-class)
- [Outputing Variables](https://svelte.dev/examples#hello-world)
- [Two Way Binding](https://svelte.dev/examples#text-inputs)
- [Class Binding](https://svelte.dev/examples#classes)

### Steps

1) Create a script tag with 2 variables one for the price and the other for the tip amount.

```html
<script>
  let price = 12.51;
  let tip = 15;
</script>
```

2) Bind the variables to the right inputs

```html
<input bind:value={tip} type="range" min="0" max="100" step="1" id="tip">
```

```html
<input bind:value={price} type="number" id="price">
```

3) Output the tip in the label

```html
<label for="tip">Tip ({tip}%)</label>
```

4) Create a function changes the tip variable to a new value.

```javascript
function changeTip(newTip) {
  tip = newTip;
}
```

6) Hook up the function to the on click event in the button tags

```html
<div class="column">
    <button on:click={() => changeTip(15)} class="button button-outline">
        15%
    </button>
</div>
<div class="column">
    <button on:click={() => changeTip(25)}  class="button button-outline">
        25%
    </button>
</div>
<div class="column">
    <button on:click={() => changeTip(30)}  class="button button-outline">
        30%
    </button>
</div>
```

7) Bind the class button-outline to show up only if the tip amount does not equal what the button text equals.

```html
<div class="column">
    <button on:click={() => changeTip(15)} class:button-outline={tip !== 15}   class="button">
        15%
    </button>
</div>
<div class="column">
    <button on:click={() => changeTip(25)} class:button-outline={tip !== 25}  class="button">
        25%
    </button>
</div>
<div class="column">
    <button on:click={() => changeTip(30)} class:button-outline={tip !== 30}  class="button">
        30%
    </button>
</div>
```

## 7) Reactivity In Svelte

- How to make a variable in svelte to calculate the tip.

### Resources

- [Code](https://github.com/phptuts/udemy-svelte-tip-calculator/tree/video-7-reactive-variable)
- [Reactive Variables](https://svelte.dev/examples#reactive-declarations)
- [toStringLocale](https://www.w3schools.com/jsref/jsref_tolocalestring_number.asp)

### Steps

1) Create a function that calculates the tip amount.

```javascript
function calculatedTip(price, tip) {
    const calcTip = (price * (tip / 100));
    return calcTip.toLocaleString('en-US', {
        style: 'currency',
        currency: 'USD'
    });
}
```

2) Create a reactive variable

```javascript
$: tipAmount = calculatedTip(price, tip);
```

3) Output the reactive variable in the template

```svelte
<h2>Calculated Tip: {tipAmount}</h2>
```

## 8) Github Pages

How to publish to github pages

### Resources

- [GH Pages](https://pages.github.com/)
- [Gh Pages NPM](https://www.npmjs.com/package/gh-pages)


### Steps

1) Import gh pages in your rollup config.

```javascript
import ghpages from 'gh-pages'
```

2) Go to the part that run only when production is on and upload to githpages

```javascript
production && terser() && ghPages.publish('public', (err) => {
      console.log(err, 'uploaded to gh pages');
    }),
```

3) Run npm run build

```bash
npm run build
```

4) Go to your github repository -> setting and find the url and make sure it's working.
