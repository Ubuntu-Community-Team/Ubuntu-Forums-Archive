---
title: "HTML gradient without images"
date: 2007-05-22
forum: Programming Talk
---

### Post by SeanTater on 2007-05-22
I wanted to set a gradient into a document without external references, so I found a way to do this that works in every browser I know of (IE, Safari, FF, Konqueror).. It works by a series of <div>'s with specific heights to make a vertical gradient; here is an example of how it works:

```

<div style='height: 0;'>
[INDENT]
<div style='background-color: rgb(255, 255, 255); height: 1px;'></div>
<div style='background-color: rgb(248, 249, 253); height: 1px;'></div>
<div style='background-color: rgb(241, 244, 252); height: 1px;'></div>
<div style='background-color: rgb(234, 238, 251); height: 1px;'></div>
<div style='background-color: rgb(227, 233, 250); height: 1px;'></div>
<div style='background-color: rgb(220, 227, 249); height: 1px;'></div>
[/INDENT]
</div>

```

I just set this code block above anything I want to have a gradient background, and the gradient extends underneath the text, because the child div's have a larger height than the parent. 

So how do I make this work in a horizontal gradient?

---

### Post by skeeterbug on 2007-05-22
Wouldn't something like this work?

```

<div style='width: 6px;'>
<div style='background-color: rgb(255, 255, 255); width: 1px;'></div>
<div style='background-color: rgb(248, 249, 253); width: 1px;'></div>
<div style='background-color: rgb(241, 244, 252); width: 1px;'></div>
<div style='background-color: rgb(234, 238, 251); width: 1px;'></div>
<div style='background-color: rgb(227, 233, 250); width: 1px;'></div>
<div style='background-color: rgb(220, 227, 249); width: 1px;'></div>
</div>

```

---

### Post by barmazal on 2007-05-23
height of DIV set to 1px won't works on many browsers, i think IE 6 have 5 or 10 px as min.

---

### Post by LaRoza on 2007-05-23
This will only work natively in Opera, Firefox and IE need plugins, but SVG is perfect for this, it it a vector graphics markup language and can be embedded in the markup (with a different namespace). Of course, this will not be a solution for a while, but it is technically, best suited for this.

---

