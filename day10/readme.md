
# 3.1 CSS Syntax, Cascade & Selectors

## What is CSS?

**CSS (Cascading Style Sheets)** is used to style HTML elements and control their color, 
size, spacing, layout, positioning, responsiveness, and overall appearance.

## Basic CSS Syntax

```css
selector {
  property: value;
}
```

Example:

```css
p {
  color: blue;
  font-size: 18px;
}
```

- `p` → Selector
- `color` → Property
- `blue` → Value

## Ways to Include CSS

### 1. Inline CSS

```html
<p style="color: red;">Hello</p>
```

### 2. Internal CSS

```html
<style>
  p {
    color: red;
  }
</style>
```

### 3. External CSS

```html
<link rel="stylesheet" href="style.css">
```

**Interview answer:**

> External CSS is generally preferred because it improves reusability, maintainability, and separation of concerns.

---

## CSS Selectors

Selectors are used to select HTML elements that we want to style.

### Tag Selector

```css
p {
  color: red;
}
```

Selects all `<p>` elements.

### Class Selector

```css
.card {
  padding: 20px;
}
```

A class can be reused on multiple elements.

### ID Selector

```css
#header {
  background: black;
}
```

An ID is generally intended for a unique element.

### Universal Selector

```css
* {
  margin: 0;
  padding: 0;
}
```

Selects all elements.

### Grouping Selector

```css
h1, h2, p {
  color: blue;
}
```

Styles multiple selectors with one rule.

---

## Combinators

### Descendant Selector

```css
.container p {
  color: red;
}
```

Selects all `<p>` elements inside `.container`.

### Child Selector

```css
.container > p {
  color: red;
}
```

Selects only direct `<p>` children.

### Adjacent Sibling

```css
h1 + p {
  color: red;
}
```

Selects the first `<p>` immediately after an `<h1>`.

### General Sibling

```css
h1 ~ p {
  color: red;
}
```

Selects `<p>` siblings that appear after `<h1>`.

---

## Cascade

The **cascade** is the process CSS uses to determine which style should be applied when multiple rules target the same element.

Important factors include:

1. Importance
2. Specificity
3. Source order

Example:

```css
p {
  color: blue;
}

p {
  color: red;
}
```

Both have the same specificity, so the later rule wins.

---

## Specificity

Specificity determines which selector has higher priority.

General order:

```text
Inline style > ID > Class/Pseudo-class/Attribute > Element
```

Example:

```css
p {
  color: blue;
}

.text {
  color: green;
}

#title {
  color: red;
}
```

The ID selector has higher specificity than the class and element selector.

### `!important`

```css
p {
  color: red !important;
}
```

It gives the declaration very high priority and can override normal cascade rules.

**Interview tip:** Avoid unnecessary use of `!important` because it can make CSS difficult to maintain.

---

## Inheritance

Some CSS properties are automatically inherited from a parent to its children.

Common inherited properties:

```text
color
font-family
font-size
line-height
```

---

# 3.2 Typography, Colors & Reusable Design Tokens

## Typography

Typography controls the appearance, readability, and spacing of text.

### Important Typography Properties

```text
font-family
font-size
font-weight
font-style
line-height
letter-spacing
word-spacing
text-align
text-decoration
text-transform
```

### `font-family`

```css
body {
  font-family: Arial, sans-serif;
}
```

Defines the font.

### `font-size`

```css
h1 {
  font-size: 32px;
}
```

Controls text size.

### `font-weight`

```css
font-weight: 400; /* normal */
font-weight: 700; /* bold */
```

Common values:

- `400` → normal
- `500` → medium
- `600` → semi-bold
- `700` → bold

### `font-style`

```css
font-style: italic;
```

### `line-height`

Controls vertical space between lines.

```css
p {
  line-height: 1.5;
}
```

## Text Properties

### `text-align`

```css
text-align: center;
```

Values: `left`, `right`, `center`, `justify`.

### `text-decoration`

```css
text-decoration: underline;
```

### `text-transform`

```css
text-transform: uppercase;
```

Values: `uppercase`, `lowercase`, `capitalize`.

### `letter-spacing`

```css
letter-spacing: 2px;
```

Controls space between characters.

### `word-spacing`

```css
word-spacing: 5px;
```

Controls space between words.

---

## Colors

### HEX

```css
color: #ff0000;
```

### RGB

```css
color: rgb(255, 0, 0);
```

### RGBA

```css
color: rgba(255, 0, 0, 0.5);
```

The fourth value controls transparency.

### HSL

```css
color: hsl(0, 100%, 50%);
```

---

## Background Properties

Important properties:

```text
background-color
background-image
background-repeat
background-position
background-size
background
```

Example:

```css
.hero {
  background-image: url("image.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
```

### `background-size`

**cover**

Fills the container. Some part of the image may be cropped.

**contain**

Shows the complete image, but empty space may remain.

---

## CSS Variables / Design Tokens

CSS variables allow us to store reusable values.

```css
:root {
  --primary-color: #2563eb;
  --spacing: 20px;
  --radius: 10px;
}

.card {
  color: var(--primary-color);
  padding: var(--spacing);
  border-radius: var(--radius);
}
```

**Interview answer:**

> CSS variables are used to store reusable values such as colors, spacing, font sizes, and border radius. They improve consistency and make maintenance easier.

---

# 3.3 Box Model, Sizing & Display

> **Very Important Interview Topic**

Every HTML element is treated as a box.

The CSS Box Model consists of:

```text
Content
   ↓
Padding
   ↓
Border
   ↓
Margin
```

## Content

The actual text, image, or other content.

## Padding

Space inside the element, between content and border.

```css
padding: 20px;
```

## Border

The line surrounding the element.

```css
border: 1px solid black;
```

## Margin

Space outside the element.

```css
margin: 20px;
```

---

## `box-sizing`

### `content-box`

Default behavior.

```css
box-sizing: content-box;
```

Width and height apply to the content area.

### `border-box`

```css
box-sizing: border-box;
```

Width and height include:

```text
Content + Padding + Border
```

Common reset:

```css
* {
  box-sizing: border-box;
}
```

**Interview answer:**

> With `content-box`, width and height apply to the content area only. With `border-box`, the specified width and height include padding and border.

---

## Width & Height

```css
width: 300px;
height: 200px;
```

Important sizing properties:

```text
min-width
max-width
min-height
max-height
```

---

## Overflow

Controls what happens when content exceeds the element's size.

```css
overflow: hidden;
```

Values:

```text
visible
hidden
scroll
auto
```

Example:

```css
.box {
  width: 200px;
  height: 100px;
  overflow: auto;
}
```

---

## Display Property

### `block`

```css
display: block;
```

Usually takes the full available width and starts on a new line.

Examples: `div`, `p`, `h1`, `section`.

### `inline`

```css
display: inline;
```

Does not normally start a new line.

Examples: `span`, `a`.

### `inline-block`

Behaves like inline content but allows width and height to be applied.

### `none`

```css
display: none;
```

Element is removed from the layout.

---

## CSS Units

### `px`

Fixed CSS pixel unit.

```css
width: 200px;
```

### `%`

Relative to a relevant containing/reference dimension.

```css
width: 50%;
```

### `rem`

Relative to the root (`html`) font size.

```css
font-size: 2rem;
```

### `em`

Relative to the current/parent font size depending on context.

### `vw`

1% of viewport width.

```css
width: 50vw;
```

### `vh`

1% of viewport height.

```css
height: 100vh;
```

---

# 3.4 Pseudo-classes, Pseudo-elements & Component States

## Pseudo-class

A pseudo-class targets an element based on its state or condition.

Important pseudo-classes:

```text
:hover
:focus
:active
:visited
:first-child
:last-child
:nth-child()
:checked
:disabled
:required
:valid
:invalid
```

### `:hover`

```css
button:hover {
  background: blue;
}
```

Applied when the pointer is over the element.

### `:focus`

```css
input:focus {
  outline: 2px solid blue;
}
```

Applied when an element receives focus.

### `:active`

```css
button:active {
  transform: scale(0.98);
}
```

Applied while an element is being activated.

---

## Structural Pseudo-classes

### `:first-child`

```css
li:first-child {
  color: red;
}
```

### `:last-child`

```css
li:last-child {
  color: blue;
}
```

### `:nth-child()`

```css
li:nth-child(2) {
  color: green;
}
```

Selects the second child.

---

## Form States

```css
input:required
input:valid
input:invalid
input:checked
input:disabled
```

Example:

```css
input:invalid {
  border: 1px solid red;
}
```

---

## Pseudo-elements

Pseudo-elements style a specific part of an element or generate content.

Important ones:

```text
::before
::after
::first-letter
::first-line
::selection
```

Example:

```css
.title::before {
  content: "★";
}
```

### Pseudo-class vs Pseudo-element

**Pseudo-class → state**

```css
button:hover
```

**Pseudo-element → specific part**

```css
p::first-letter
```

---

# 3.5 Responsive Landing Page Recreation

This means converting a reference design/screenshot into a responsive webpage using HTML and CSS.

Important concepts:

- Semantic HTML
- Typography
- Colors
- Spacing
- Box Model
- Reusable classes
- Component hierarchy
- Responsive widths
- Fluid media
- Alignment
- DevTools
- Refactoring duplicate CSS

Example:

```html
<header></header>

<main>
  <section class="hero"></section>
  <section class="features"></section>
  <section class="about"></section>
</main>

<footer></footer>
```

Responsive image:

```css
img {
  max-width: 100%;
  height: auto;
}
```

---

# 4.1 Flexbox Fundamentals

> **Extremely Important**

**Flexbox** is a one-dimensional CSS layout system used to arrange elements 
in a row or column.

Basic:
css
.container {
  display: flex;
}

## Flexbox Properties

### `display`

```css
display: flex;
```

Creates a flex container.

### `flex-direction`

```css
flex-direction: row;
```

Values:

```text
row
row-reverse
column
column-reverse
```

### `justify-content`

Controls alignment along the main axis.

```css
justify-content: center;
```

Important values:

```text
flex-start
flex-end
center
space-between
space-around
space-evenly
```

### `align-items`

Controls alignment along the cross axis.

```css
align-items: center;
```

Values:

```text
flex-start
flex-end
center
stretch
baseline
```

### `gap`

Creates space between flex items.

```css
gap: 20px;
```

### `flex-wrap`

Controls whether items can move to another line.

```css
flex-wrap: wrap;
```

Values:

```text
wrap
nowrap
wrap-reverse
```

---

## Flex Item Properties

### `flex-grow`

Controls how much an item can grow.

```css
.item {
  flex-grow: 1;
}
```

### `flex-shrink`

Controls how much an item can shrink.

```css
flex-shrink: 1;
```

### `flex-basis`

Defines the initial size of a flex item.

```css
flex-basis: 200px;
```

### `flex`

Shorthand for flex-grow, flex-shrink and flex-basis.

```css
flex: 1;
```

### `align-self`

Overrides cross-axis alignment for an individual item.

```css
.item {
  align-self: center;
}
```

---

## `justify-content` vs `align-items`

If:

```css
flex-direction: row;
```

Then generally:

```text
justify-content → main axis
align-items     → cross axis
```

If direction changes to `column`, the axes change too.

**Interview answer:**

> `justify-content` works on the main axis, while `align-items` works on the cross axis.

---

# 4.2 CSS Grid Fundamentals

**CSS Grid** is a two-dimensional layout system that allows us to control rows and columns.

Basic example:

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

Creates three equal columns.

## Grid Properties

### `grid-template-columns`

```css
grid-template-columns: 200px 1fr 1fr;
```

Defines columns.

### `grid-template-rows`

```css
grid-template-rows: 100px 200px;
```

Defines rows.

### `gap`

```css
gap: 20px;
```

### `row-gap`

```css
row-gap: 20px;
```

### `column-gap`

```css
column-gap: 20px;
```

---

## `fr` Unit

`fr` means **fraction of available space**.

```css
grid-template-columns: 1fr 2fr;
```

The available space is divided into 3 fractions:

```text
1 part → first column
2 parts → second column
```

## `repeat()`

Instead of:

```css
grid-template-columns: 1fr 1fr 1fr;
```

we can write:

```css
grid-template-columns: repeat(3, 1fr);
```

## `minmax()`

Defines minimum and maximum size.

```css
grid-template-columns:
  repeat(3, minmax(200px, 1fr));
```

## `auto-fit`

Very useful for responsive cards.

```css
grid-template-columns:
  repeat(auto-fit, minmax(200px, 1fr));
```

It automatically adjusts the number of columns based on available space.

---

## Flexbox vs Grid

| Flexbox | Grid |
|---|---|
| One-dimensional | Two-dimensional |
| Row OR column | Rows + columns |
| Component-level layouts | Page-level layouts |
| Navigation/cards | Dashboard/gallery |

**Interview answer:**

> I use Flexbox when I mainly need one-dimensional alignment, and CSS Grid when I need control over both rows and columns.

---

# 4.3 Positioning, Layering & Responsive Media

Important `position` values:

```text
static
relative
absolute
fixed
sticky
```

## `static`

Default positioning.

```css
position: static;
```

## `relative`

The element remains in normal flow and can be positioned using `top`, `right`, `bottom`, and `left`.

```css
.box {
  position: relative;
  top: 10px;
}
```

It is also commonly used as the containing reference for an absolutely positioned child.

## `absolute`

The element is removed from normal document flow.

```css
.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

Common pattern:

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

## `fixed`

Positioned relative to the viewport.

```css
button {
  position: fixed;
  bottom: 20px;
  right: 20px;
}
```

It normally stays in place while scrolling.

## `sticky`

The element behaves normally until it reaches a specified threshold, then sticks within its scrolling context.

```css
.header {
  position: sticky;
  top: 0;
}
```

---

## `z-index`

Controls stacking order when elements overlap.

```css
.modal {
  z-index: 1000;
}
```

A higher `z-index` generally appears above a lower one within the relevant stacking context.

---

## Responsive Images

```css
img {
  max-width: 100%;
  height: auto;
}
```

This prevents images from overflowing their containers.

### `object-fit`

Used to control how replaced content such as images fits inside its box.

```css
img {
  width: 300px;
  height: 200px;
  object-fit: cover;
}
```

Important values:

```text
fill
contain
cover
none
scale-down
```

### `object-position`

Controls the position of the content inside its box.

```css
object-position: center;
```

---

## Overflow Management

Important properties:

```text
overflow
overflow-x
overflow-y
```

Example:

```css
.container {
  overflow-x: hidden;
}
```

---

# 4.4 Responsive Design, Media Queries & Motion

## Responsive Design

Responsive design means creating a website that adapts to different screen sizes and devices.

```text
Mobile
Tablet
Desktop
```

## Viewport Meta Tag

Very important for responsive websites:

```html
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0"
>
```

---

## Media Queries

Media queries apply CSS based on conditions such as viewport width.

```css
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
}
```

Meaning:

> Apply these styles when the viewport is 768px or smaller.

---

## Mobile-First Design

In mobile-first design, we write the base CSS for smaller screens first and then add styles for larger screens.

```css
.card {
  width: 100%;
}

@media (min-width: 768px) {
  .card {
    width: 50%;
  }
}
```

**Interview answer:**

> Mobile-first means designing for smaller screens first and progressively enhancing the layout for larger screens using media queries.

---

## Transitions

Transitions create smooth changes between CSS states.

```css
button {
  transition: background-color 0.3s ease,
              transform 0.3s ease;
}

button:hover {
  transform: scale(1.05);
}
```

Important properties:

```text
transition-property
transition-duration
transition-timing-function
transition-delay
transition
```

---

## Transform

Used to visually move, rotate, scale, or skew an element.

```css
transform: translateX(20px);
```

Important functions:

```text
translate()
scale()
rotate()
skew()
```

Example:

```css
.card:hover {
  transform: translateY(-5px);
}
```

---

## CSS Animation

Animations use `@keyframes`.

```css
@keyframes slide {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(100px);
  }
}

.box {
  animation: slide 2s ease infinite;
}
```

Important properties:

```text
animation-name
animation-duration
animation-delay
animation-iteration-count
animation-direction
animation-timing-function
animation-fill-mode
animation
```

---

## Transition vs Animation

**Transition:** Used mainly for a smooth change between two states.

**Animation:** Uses `@keyframes` and can have multiple stages.

**Interview answer:**

> Transition is generally used for smooth state changes, while animation uses keyframes to define a sequence of changes.

---
z
# ⭐ Most Important Properties to Memorize

```text
display
position
top / right / bottom / left
z-index

width / height
min-width / max-width
min-height / max-height

margin
padding
border
box-sizing
overflow

color
background
font-family
font-size
font-weight
line-height
text-align

flex-direction
justify-content
align-items
align-self
flex-wrap
flex-grow
flex-shrink
flex-basis
gap

grid-template-columns
grid-template-rows
gap
minmax()
repeat()
auto-fit

object-fit
object-position

transform
transition
animation


