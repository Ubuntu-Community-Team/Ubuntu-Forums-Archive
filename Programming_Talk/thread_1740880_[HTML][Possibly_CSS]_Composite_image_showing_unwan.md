---
title: "[HTML][Possibly CSS] Composite image showing unwanted grid lines"
date: 2011-04-27
forum: Programming Talk
---

### Post by Pyro.699 on 2011-04-27
Hey...

A picture is worth 1000 words :)
[img]http://forums.allblizz.com/pyro/Messy%20Image.png[/img]

I have used *border: none*. I even tried setting *border-color: #FFF* in the hopes that id know it was a border issue. It wasnt... it still showed black lines.

Thanks
~Cody

---

### Post by simeon87 on 2011-04-27
Try border-style: none; on the images.

---

### Post by Pyro.699 on 2011-04-27
Same result, nice try though.

---

### Post by Pyro.699 on 2011-04-27
Interesting development. The site looks fine if i view it from a windows computer. Both using firefox.

---

### Post by BkkBonanza on 2011-04-28
You'll probably need to show a code sample to get help with this. Other than the obvious border setting perhaps some difference in sizing off by 1 could cause something like this but without some actual css/html code how can anyone know what may be wrong...

---

### Post by Pyro.699 on 2011-04-28
Sure thing :)

Its written using django... so here is the template that generates the table data.
[php]
<table border="0" align="center" cellpadding="0" cellspacing="0">
{% for y in 15|get_range %}<tr>{% for x in 15|get_range %}
<td><img src="" style="display: block; border-style: none" pos="{{ x }},{{ y }}" class="im_block im_scale" md5="null" /></td>
{% endfor %}</tr>{% endfor %}
</table>
[/php]
If you find it confusing, it just makes a table with 15 rows, 15 columns... and creates a pos="x,y"... pretty straight forward.

I do use firebug; here are the inherited style properties from the style-sheet.
```

element.style{
    border-style: none;
    display: block;
}

.im_scale{
    border-color: white;
    height: auto !important;
    width: 100%;
}

img{
    border: medium none;
}

*{
    margin: 0;
    padding 0;
}

Inherited from table:
table{
    border-collapse: collapse;
    border-spacing: 0;
    text-align: left;
}

Inherited from body.home:
body{
    font: "13px/1.5 "Helvetica Neue",Helvetica,Arial,sans-serif";
}
body{
    color: #ACBED4;
}

```

I do see how the border: is defined as "medium none" but here is its computated values.
```

-Text-
    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif
    font-size: 13px
    font-weight: 400
    font-style: normal
    color: #ACBED4
    text-transform: none
    text-decoration: none
    letter-spacing: normal
    word-spacing: 0
    line-height: 19.5px
    text-align: left
    vertical-align: baseline
    direction: ltr
    -Background-
    background-color: transparent
    background-image: none
    background-repeat: repeat
    background-position: 0 0
    background-attachment: scroll
    opacity: 1
-Box Model-
    width: 62.6667px
    height: 39.1667px
    top: auto
    right: auto
    bottom: auto
    left: auto
    margin-top: 0
    margin-right: 0
    margin-bottom: 0
    margin-left: 0
    padding-top: 0
    padding-right: 0
    padding-bottom: 0
    padding-left: 0
    border-top-width: 0
    border-right-width: 0
    border-bottom-width: 0
    border-left-width: 0
    border-top-color: #FFFFFF
    border-right-color: #FFFFFF
    border-bottom-color: #FFFFFF
    border-left-color: #FFFFFF
    border-top-style: none
    border-right-style: none
    border-bottom-style: none
    border-left-style: none
    box-shadow: none
-Layout-
    position: static
    display: block
    visibility: visible
    z-index: auto
    overflow-x: visible
    overflow-y: visible
    white-space: normal
    clip: auto
    float: none
    clear: none
-Other-
    cursor: auto
    list-style-image: none
    list-style-position: outside
    list-style-type: disc
    marker-offset: auto

```

That's probably over-kill for information. But please let me know if there are any other things you need to know.

Thanks
~Cody

---

### Post by BkkBonanza on 2011-04-28
I don't know anything about Django but two things come to mind immediately. 

First, it seems like an "off by one" error so I would check your code for mismatch of image size and x,y position remembering that position starts at 0 not 1. 

Second, you don't need to (and shouldn't) use a table for this and hence, no need to calculate a position for tiles at all.  You can just output img elements in sequence  and use style attributes of "display:block" and "display:inline" to control where they wrap (at end of row). By having two styles defined one for normal and one for end-of-row you can just appply the style for end-of-line once for each 15 tiles output and that will cause them to self align (without numeric positioning).

---

### Post by Pyro.699 on 2011-04-28
I need to have the x,y coordinates documented. Every minute jquery sends the current data to the server, and the server only sends back squares that need to be updated, thus increasing image update speed and lowering bandwidth consumption.

I know all of the images are the exact same size. They are processed serverside, and returned in base64 format then converted to image via [http://en.wikipedia.org/wiki/Data:_URI_scheme#HTML](http://en.wikipedia.org/wiki/Data:_URI_scheme#HTML)

Although the table might be a bit excessive, it was the easiest way xD

---

### Post by BkkBonanza on 2011-04-28
Ah, I see. Another way would be to give each tile an element "id" based on position and then you can access each one directly by knowing it's id. eg. 

<img id="t0101" class="midrow" src="..." > 
<img id="t0102" class="midrow" src="..." > 
<img id="t0103" class="rowend" src="..." >

Now you can update a tile with js code refering to id. But just another idea as there's always many ways to do things.

---

### Post by Pyro.699 on 2011-04-28
Well, everything works right now. And on a windows pc it looks fine. So i think its something much deeper than the html code that it is being displayed with.

It cant be a border because i specified the border color to be white
It cant be the tables background color, because there is none, it would be transparent

I could have done that (with regards to the id) but jquery makes selectors very easy :)
```

                    $(".im_block[pos="+x[i]+","+y[i]+"]").attr({
                        src: "data:image/png;base64,"+b64,
                        md5: md5
                    })

```

---

### Post by BkkBonanza on 2011-04-28
Have you tried twiddling with style values in Firebug? Maybe you'll find a change that alters how the blocks show/align. It's interesting it works in Windows but I guess there's always small (annoying) variances in rendering.

Edit: hold the phone... I just noticed you said the lines only show when the image contains only non-solid pixel content. That's really weird and suggests something in the base64 decoding is altering the image width/height. Maybe some decode error is causing an extra pixel row/col that changes the size of tile. Have a look at Firebug tiles to see if some show up as bigger by one in width/height?

---

### Post by Pyro.699 on 2011-04-28
I have tried that. I even disabled all of the styles that were associated with the images; still got the borders...

But something else that is interesting, is how the lines ONLY appear on images that have solid color...

---

### Post by BkkBonanza on 2011-04-28
see my update to last comment ... done after going back to original details.

---

### Post by Pyro.699 on 2011-04-28
I have taken a look at each image; and they are all the exact same size.

How-ever remember that this renders perfectly fine on a windows computer.

---

### Post by fdrake on 2011-04-28
try 

```
outline-style:none;
```?

---

### Post by bashologist on 2011-04-28
Too tired to examine the entire code but I see a table so maybe try this css on the table.
border-collapse
border-spacing

Also another possibility html like this

<img ...><img ...><img ...>

rather than

<img ...>
<img ...>
<img ...>

Try to recreate using as little code as possible to narrow down the possibilities.

---

