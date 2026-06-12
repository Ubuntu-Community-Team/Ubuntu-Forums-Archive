---
title: "Help wanted with svg path syntax"
date: 2012-11-03
forum: Programming Talk
---

### Post by vasa1 on 2012-11-03
I'm trying to understand a little about svg and would appreciate some help in understanding the syntax in drawing a relatively simple path involving just straight lines.

While I get that **h** or **v** allow for abbreviated code because there's no need to specify y for a horizontal line and x for a vertical line, I can't understand how "**-**" works in the examples below which draw two arrows, one red and blue when the code is saved as test.svg and viewed in a browser such as Firefox or Chrome.

```
<svg xmlns="http://www.w3.org/2000/svg">
<path d="m20 15-5 5-5-5h3v-7h4v7h3z" fill="blue"/>
<path d="m12 8-5-5-5 5h3v7h4v-7h3z" fill="red"/>
</svg>
```

I can draw the blue arrow in a simple way (code below) but I'd like to understand the shorthand code ...

```
<svg xmlns="http://www.w3.org/2000/svg">
<path d="M15 8 19 8 19 15 22 15 17 20 12 15 15 15z" fill="blue"/>
<path d="m12 8-5-5-5 5h3v7h4v-7h3z" fill="red"/>
</svg>
```

---

### Post by Vaphell on 2012-11-03
aren't these, you know, simple negative numbers?
i pasted your code into [http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html)
and it parses the example to this:
```
<svg width="22" height="20" xmlns="http://www.w3.org/2000/svg">

 <g>
  <title>Layer 1</title>
  <path id="svg_1" fill="blue" d="m15,8l4,0l0,7l3,0l-5,5l-5,-5l3,0l0,-7z"/>
  <path id="svg_2" fill="red" d="m12,8l-5,-5l-5,5l3,0l0,7l4,0l0,-7l3,0z"/>
 </g>
</svg>
```

---

### Post by vasa1 on 2012-11-03
> **Vaphell said:**
> aren't these, you know, simple negative numbers?
i pasted your code into [http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html)
and it parses the example to this:
```
<svg width="22" height="20" xmlns="http://www.w3.org/2000/svg">

 <g>
  <title>Layer 1</title>
  <path id="svg_1" fill="blue" d="m15,8l4,0l0,7l3,0l-5,5l-5,-5l3,0l0,-7z"/>
  <path id="svg_2" fill="red" d="m12,8l-5,-5l-5,5l3,0l0,7l4,0l0,-7l3,0z"/>
 </g>
</svg>
```
Thanks for your prompt reply! I wished I'd asked earlier :)

---

### Post by vasa1 on 2012-11-04
1. That svg-edit link is wonderful.
2. And reading more indicates that the cryptic syntax is known as "Backus-Naur Form".

---

### Post by vasa1 on 2012-11-05
Pasting code from something created by Inkscape into svg-edit and then applying changes automatically performs a scour!

---

