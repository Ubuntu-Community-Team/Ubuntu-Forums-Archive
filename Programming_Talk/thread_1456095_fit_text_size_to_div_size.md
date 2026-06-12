---
title: "fit text size to div size"
date: 2010-04-16
forum: Programming Talk
---

### Post by Ryland Taylor on 2010-04-16
Hi, I have a navigation bar at the top of a page, and there are a few links in it. basic example of what I have:

html:
```
<div id="navigation">
Home | About Us | Faculty and Staff | Academics | Student Life | Sports and Extracurriculars | Contact Us | VUSD
</div>
```

css:
```
#navigation{
    width: 800px;
    height: 30px;
}
```

Now what I want to do is make it so that the text size for the navigation bar is as big as possible, without being to big for the width or height of the div. is this easy to do?

---

### Post by gzarkadas on 2010-04-16
Since your nav-bar is fixed pixel size, you can add a `font-size' attribute, inside the "#navigation" style definition and play with its value (replace ? below with a number):

```
font-size: ?px
```Keep this under your pillow: [http://www.w3.org/TR/CSS21/](http://www.w3.org/TR/CSS21/)

---

### Post by Ryland Taylor on 2010-04-17
I had a font size attribute before, but what was perfect in firefox and safari, was too big for google chrome. but making it smaller for chrome made it smaller than I wanted for firefox and safari (and I haven't even tested with IE yet.) There's no way to make the font size relative, sort of like how you can use percentages for the size of divs and images?

---

### Post by gzarkadas on 2010-04-17
Yes it is, use `em' or percentage. The  link describes them both. However, if you want it to play well in all available browsers, you should in general allow some space, because as you have already noticed their rendering of css is not exactly the same.

---

