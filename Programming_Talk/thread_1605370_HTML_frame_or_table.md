---
title: "HTML frame or table?"
date: 2010-10-25
forum: Programming Talk
---

### Post by rcayea on 2010-10-25
Hey everyone,

First, I hope I am not in the wrong forum for this question. I am creating my web page and I was wondering if it would be best to use the table tag or the frame tag for what I would like to accomplish.

The picture I have attached shows what I want to do. I want to add some squares on the right that would later hold various links for two separate topics. 

Thanks,
Randy

---

### Post by r-senior on 2010-10-25
Frames have their uses but have fallen out of favour and don't play nicely with bookmarks. Tables were always designed for displaying data but have been abused as a layout tool, largely because there was no better option.

These days CSS is the way to go - flexibility, separation of content from presentation, accessibility, reusability, consistency across pages.

[http://www.w3schools.com/css/]("http://www.w3schools.com/css/")

[http://www.csszengarden.com/]("http://www.csszengarden.com/")

---

### Post by rcayea on 2010-10-25
I do know some CSS and I figured I would end up using that. But, thanks for the info.

---

### Post by ja660k on 2010-10-25
tables are so 90s

use divs and css :)

---

### Post by rcayea on 2010-10-25
LOL! But I love the 90s. Just kidding. I do realize I would have to use CSS. I actually have been, but I am not sure what attribute to use. 

Any thoughts?

---

### Post by SeijiSensei on 2010-10-25
> **rcayea said:**
> LOL! But I love the 90s. Just kidding. I do realize I would have to use CSS. I actually have been, but I am not sure what attribute to use.

Use a class and DIVs:

```

<style>
.mybox { CSS styles for box location, borders, colors, etc. }
</style>

<div class='mybox'>
Text
</div>

```

That said, I still use tables a lot for page layout.  I'm just so 90's.

CSS Standard: [http://www.w3.org/TR/CSS2/](http://www.w3.org/TR/CSS2/)
CSS for boxes: [http://www.w3.org/TR/CSS2/box.html](http://www.w3.org/TR/CSS2/box.html)

---

### Post by rcayea on 2010-10-25
OK. Thanks. I'll give it a shot and see how bad I do. :)

---

### Post by Finalfantasykid on 2010-10-25
The only frame that I find useful sometimes is the iframe, although should only be used if it actually makes sense(like for chatboxes and such).  But for everything else I use a combination of tables and divs.

---

