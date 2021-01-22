## Quick start

``` 
npm i sass-easy-grid
```

- Create _grid.scss file with content:

```
@forward './node_modules/sass-easy-grid/sass-easy-grid';
```

###### or if you're using webpack:

```
@forward '~sass-easy-grid';
```

- Import the file you just created into your project scss file:

```
@use './grid';
```
***

### Now you can use it:
<div style="display: flex;">
    <div style="margin-right: 20px">
        <h6>Scss:</h6>
        <pre><code class="language-c">@use './grid';<br>
.row {
  @include grid.row();
}<br>
.col {
  @include grid.col(1,-1);
  @include grid.col-xxl(1,9);
}
</code></pre>
    </div>
    <div style=";">
        <h6>Output css:</h6>
        <pre><code class="language-c">.row {
  grid-template-columns: repeat(12, 1fr);
  grid-column-gap: 30px;
}<br>
.col {
  grid-column: 1/-1;
}<br>
@media screen and (min-width: 1400px) {
  .col {
    grid-column: 1/10;
  }
}</code></pre>
    </div>
</div>


**sass-easy-grid provides you with a set of mixins that make grid work easy:**

- container($content-box: true) - **Сreates a bounding container.**
   - $content-box: sets box-sizing: content-box. Set false if don't wanna use it.
   ```
   box-sizing: content-box;
   ```
   
***

- row() - **Creates a grid from the given columns (default 12).**

***

- col($start, $end) - **Sets the position of an element on the grid.**
   - $start: element start position.
   - $end: element end position.

- col-sm($start, $end) - **Sets the position of an element on the small displays.**
- col-md($start, $end) - **Sets the position of an element on the medium displays.**
- col-lg($start, $end) - **Sets the position of an element on the large displays.**
- col-xl($start, $end) - **Sets the position of an element on the extra-large displays.**
- col-xxl($start, $end) - **Sets the position of an element on the extra-extra-large displays.**

***

- justify($value) - **Aligns all elements in a row horizontally.**
   - $value: Takes one of the values **[start, end, center]**

- align($value) - **Aligns all elements in a row vertically.**

- justify-self($value) - **Aligns the element horizontally**

- align-self($value) - **Aligns the element vertically.**  


## Options

**You can set own grid options:**

###### #_grid.scss
```
@forward '~sass-easy-grid' with (
  $columns: 12, //set columns count
  $container-max-width-xxl: 1170px, //sets container max width on extra-extra-large displays,
  $container-max-width-md: 600px, //sets container max width on medium displays,
  $grid-breakpoint-sm: 530px // sets grid breakpoint on small displays
);
```

#### More options:

```$option-name: default-value```

- $grid-breakpoint-sm: 576px;
- $grid-breakpoint-md: 768px;
- $grid-breakpoint-lg: 992px;
- $grid-breakpoint-xl: 1200px;
- $grid-breakpoint-xxl: 1400px;
- $grid-columns: 12;
- <span style="color:#FF7575">$grid-column-gap</span>: 30px;
- $container-max-width-sm: 540px;
- $container-max-width-md: 720px;
- $container-max-width-lg: 960px;
- $container-max-width-xl: 1140px;
- $container-max-width-xxl: 1320px;
- $container-padding: <span style="color:#FF7575">$grid-column-gap</span> / 2;