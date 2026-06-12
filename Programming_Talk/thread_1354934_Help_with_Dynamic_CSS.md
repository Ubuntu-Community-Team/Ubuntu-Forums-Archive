---
title: "Help with Dynamic CSS"
date: 2009-12-14
forum: Programming Talk
---

### Post by Black Mage on 2009-12-14
I am having trouble making a 3 column layout. What I am trying to accomplish is when there is no left or right column, the main column takesup all the space in the container. But if there is a left or right column added, then the main container only takes up the (Full Width)-(Width of column)=Width of Main Container. This will work for any length the left/right containers are. The problem is, why I try different layouts never seems to work. I've tried percentages, min/max length, etc.
Can someone give me any advice on this?

---

### Post by Hellkeepa on 2009-12-14
HELLo!

You need to use a bit of JavaScript for this, I'm afraid. CSS simply does not support the logic needed for this.

Happy syncin'!

---

### Post by TheBuzzSaw on 2009-12-14
> **Hellkeepa said:**
> HELLo!

You need to use a bit of JavaScript for this, I'm afraid. CSS simply does not support the logic needed for this.

Happy syncin'!

Actually, there are many things you can do in CSS that support this guy's request. Gimme a moment; I will post up some sample CSS in a bit.

(I gotta run to class at the moment, but I shall return!)

---

### Post by Hellkeepa on 2009-12-14
HELLo!

Well... You could just use floats on the sidebars, and add the block elements if they're needed. However, this won't work too well with margins, or advanced layouts. So it really depends upon what the OP wants to do in addition to this.

That said, I am really interested in seeing your suggestion. Hopefully I'll learn something as well. :-)

Happy codin'!

---

### Post by Black Mage on 2009-12-14
> **TheBuzzSaw said:**
> Actually, there are many things you can do in CSS that support this guy's request. Gimme a moment; I will post up some sample CSS in a bit.

(I gotta run to class at the moment, but I shall return!)

Thanks a lot!!!!! Can't wait

---

### Post by TheBuzzSaw on 2009-12-14
index.html
[php]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Three Column Transformations</title>
        <link href="theme.css" rel="stylesheet" />
    </head>
    <body>
        <div id="page-container">
            <div class="zone">
                <p class="left column">left</p>
                <p class="right column">right</p>
                <p class="main column">main</p>
            </div>
            
            <div class="zone">
                <p class="left column">left</p>
                <p class="main column">main</p>
            </div>
            
            <div class="zone">
                <p class="right column">right</p>
                <p class="main column">main</p>
            </div>
            
            <div class="zone">
                <p class="main column">main</p>
            </div>
        </div>
    </body>
</html>
[/php]

theme.css
```
* { margin: 0; padding: 0; }
fieldset, img { border: 0; }

#page-container
{
    margin: 0 auto;
    width: 960px;
}

.zone
{
    margin: 0.5em 0;
    border: 1px dotted black;
    padding: 10px;
    clear: both;
    overflow: hidden;
}

.zone .column
{
    border: 1px dashed black;
    padding: 10px;
    width: 100px;
}

.zone .column.left
{
    float: left;
    margin-right: 10px;
}

.zone .column.right
{
    float: right;
}

.zone .column.main
{
    width: 916px;
}

.zone .column.left + .column.main,
.zone .column.right + .column.main
{
    float: left;
    width: 784px;
}

.zone .column.left + .column.right + .column.main
{
    width: 652px;
}

```

As long as your left/right columns come first, the CSS will automatically adjust the column widths.

I tested this code in Firefox 3.5! :)

This will not work fluidly based on *varying* column widths. It just lets you have preset left/right columns that can appear. You can accommodate more layout alternatives using the proper CSS.

---

