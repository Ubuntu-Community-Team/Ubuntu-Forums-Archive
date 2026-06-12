---
title: "CSS trick needed for &quot;header&quot;"
date: 2007-12-07
forum: Programming Talk
---

### Post by pmasiar on 2007-12-07
I have web page, and need to display 3 values: "Home" link in upper left corner, "(Prototype)" in the middle, and "[version]" in upper right corner.

All this should live in a box (class "standard-box", centered in the middle of the page, with nice rounded corners: crossplatform solution would be nice too)

```

<body class="yui-skin-sam">
    <div align="center">
      <div align="center" style="width: 900px " id="top1000">
        <div align="center">
          <div align="justify" style="min-height: 180px;" id="search" class="standard-box">
            <div align="left">
               <a href="/">Home</a>
            </div>
            <div align="center" id="subtitle">
              <h1>(Prototype)</h1>
            </div>
            <div align="right">
              [Demo]
           </div>
(closing all divs)

```

Right now I have those 3 items in different lines (not pretty). Is it possible to have them on "same line"? What is CSS magic to do it?

Thanks!

---

### Post by ThinkBuntu on 2007-12-07
The easiest way would be to float the three, each taking a third of the page's width. Personally, I see this as a case, when a light table is excusable even though the content is not tabular.

```

/* CSS */
#header {
width: 100%;
}

#header .block {
width: 33%;
float: left;
display: block;
}

.clear {
clear: left;
}

.left {
text-align: left;
}

.center {
text-align: center;
}

.right {
text-align: right;
}

```
```

<!-- HTML -->
<div id="header>
<div class="block left">
Left text
</div>
<div class="block center">
Center text
</div>
<div class="block right">
Right text
</div>
<div class="clear"></div>
</div>

```
Alternatively, apply clear: left to the element that follows the header. Using the empty clear tag makes the header more portable, which is why I use it here.

p.s. indentation has been spared because it's a pain to use in a Textarea.

p.p.s. Swing by CSSForums if you have more questions like these...always happy to help :^)

EDIT: I explicitly declared "display: block" for the block class so that you can use <a>s up there instead of <div>s. It is a bit redundant but is more flexible. If you're using just links up there, it will result in cleaner HTML.

---

