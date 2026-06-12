---
title: "infinite css"
date: 2012-05-20
forum: Programming Talk
---

### Post by maclenin on 2012-05-20
I am wondering whether there's a way to...

[B]#div0,
#div1,
#div2,
...
#divAdInfinitum {display:inline-block;}[/B]

Essentially, I have a flexible-height web page upon which I am displaying (via onload or onclick) different sets of (varying quantities of) thumbnails. I would like to configure css to allow for the display of an infinite number of thumbnails (just in case?) - without having to type out **#div0, #div1, #div2 ...** for all infinity (or even 100) of them....

Thanks for any thoughts!

---

### Post by Zugzwang on 2012-05-20
Just declare one type and use this one type for every thumbnail. If you need different settings for every single thumbnail, then you are using HTML+CSS in a way it isn't supposed to be used, which is a common cause for problems.

---

### Post by maclenin on 2012-05-20
**Zugzwang!**

Thanks for your reply.

Perhaps, I should be a bit more specific....

In "short", my web page displays thumbnails and associated larger images - slideshow-esque....

click button1 - the owl set of thumbnails (and a larger image) is displayed.
click button2 - the tiger set of thumbnails (and a larger image) is displayed.
click button3 - the turtle set of thumbnails (and a larger image) is displayed.

Each **[COLOR="DarkGreen"]thumbnail[/COLOR]** - within a specific **[COLOR="DarkOrange"]set[/COLOR]** - has a uniquely "defined" javascript **[COLOR="DarkRed"]function[/COLOR]**, which calls a specific larger image.

So...owl, tiger and turtle, oh my....

**[COLOR="DarkOrange"]button1. OWL set[/COLOR]**
**<div id="div0" onclick="[B][COLOR="DarkRed"]display_image(0);[/COLOR]**"><img id="tn0" src="**[COLOR="DarkGreen"]thumbnail8[/COLOR]**.jpg"></div>
<div id="div1" onclick="**[COLOR="DarkRed"]display_image(1);[/COLOR]**"><img id="tn1" src="**[COLOR="DarkGreen"]thumbnail9[/COLOR]**.jpg"></div>
<div id="div2" onclick="**[COLOR="DarkRed"]display_image(2);[/COLOR]**"><img id="tn2" src="**[COLOR="DarkGreen"]thumbnail15[/COLOR]**.jpg"></div>
...
<div id="divX" onclick="display_image(X);"><img id="tnX" src="thumbnailX.jpg"></div>[/B]

**[COLOR="DarkOrange"]button2. TIGER set[/COLOR]**
**<div id="div0" onclick="[B][COLOR="DarkRed"]display_image(0);[/COLOR]**"><img id="tn0" src="**[COLOR="DarkGreen"]thumbnail123[/COLOR]**.jpg"></div>
<div id="div1" onclick="**[COLOR="DarkRed"]display_image(1);[/COLOR]**"><img id="tn1" src="**[COLOR="DarkGreen"]thumbnail145[/COLOR]**.jpg"></div>
<div id="div2" onclick="**[COLOR="DarkRed"]display_image(2);[/COLOR]**"><img id="tn2" src="**[COLOR="DarkGreen"]thumbnail260[/COLOR]**.jpg"></div>
...
<div id="divX" onclick="display_image(X);"><img id="tnX" src="thumbnailX.jpg"></div>[/B]

**[COLOR="DarkOrange"]button3. TURTLE set[/COLOR]**
**<div id="div0" onclick="[B][COLOR="DarkRed"]display_image(0);[/COLOR]**"><img id="tn0" src="**[COLOR="DarkGreen"]thumbnail345[/COLOR]**.jpg"></div>
<div id="div1" onclick="**[COLOR="DarkRed"]display_image(1);[/COLOR]**"><img id="tn1" src="**[COLOR="DarkGreen"]thumbnail367[/COLOR]**.jpg"></div>
<div id="div2" onclick="**[COLOR="DarkRed"]display_image(2);[/COLOR]**"><img id="tn2" src="**[COLOR="DarkGreen"]thumbnail1789[/COLOR]**.jpg"></div>
...
<div id="divX" onclick="display_image(X);"><img id="tnX" src="thumbnailX.jpg"></div>[/B]

NB:
 
*There could be 100s / 1000s of thumbnails associated with each of the sets.

*The thumbnail src details will change, depending on which set is selected.

*The javascript onclick event will NOT change in the HTML. However, the  "purpose" of the function, itself, WILL be modified in the .js file to match the set of thumbnails currently selected.

*I feel like I need to create multiple (infinite) unique divs (in the css) for multiple unique thumbnails because of the 1 to 1 function to (bring up a unique image for a specific) thumbnail relationship that I've described....

Danke, nochmals, for the advice.

---

### Post by Bachstelze on 2012-05-20
Unless I missed something...

<div style="display:inline-block" onclick="display_image(0);"><img id="tn0" src="thumbnail123.jpg"></div>

---

### Post by Bachstelze on 2012-05-20
If you really need a CSS and you know in advance how many elements you will need, you can just PHP it:

[php]
<?php
header("Content-type: text/css");

$n = 30;
for ($i = 0; $i < $n; $i++) {
    echo "#div$i,\n";
}
echo "#div$n {display:inline-block;}\n";
[/php]

Of course the point is that you can get $n from somewhere else, not to hardcode it.

---

### Post by Barrucadu on 2012-05-20
Just give every <div> a common class and use that.

---

### Post by Zugzwang on 2012-05-21
> **Barrucadu said:**
> Just give every <div> a common class and use that.

Indeed.

@OP: I think that you are mixing up "class" and "id". You might want to give your div's different ids, but for CSS, the class attribute is of relevance. So you define something like:
```

#divStyle {display:inline-block;}

```
in your CSS file and then use code like this for the actual divs:
```

<div id="div0" class="divStyle" onclick="display_image(0);"><img id="tn0" src="thumbnail8.jpg"></div>
<div id="div1" class="divStyle" onclick="display_image(1);"><img id="tn1" src="thumbnail9.jpg"></div>
<div id="div2" class="divStyle" onclick="display_image(2);"><img id="tn2" src="thumbnail15.jpg"></div>

```

---

### Post by maclenin on 2012-05-22
**Zugzwang!**

I hear you re: class vs. id - and though I have yet to fully grasp the nuances - I would like to offer this latest sample of infinite CSSing - thanks to your (**ZBBBZ!**) collective insights (and some referenced googling).

*I have (many more than) 6 images, as part of a javascript array - each image is tagged set "1", set "2" or set "3" (and so on). See: **gallery.js**.

*Upon selecting set 1 or set 2 or set 3, thumbnails of the selected set are laid out in a thumbnails "pane" and the large image of the "first" thumbnail of the selected set is displayed in its large_image pane - all in **gallery.html**.

*The thumbnails' divs are defined (onload in the html), based on the number of images in the image array by the function add_css() in **gallery_css.js** (similar to php, **Bachstelze!**). I am not using both a class and an id for the thumbnail divs as it seems excessive, if the id (rather than the class) can serve as both the javascript and "styling" reference?

**gallery.html**
```

<!--body-->
<body onload="add_css(); display_set(1);">

<!--large_image-->
<div><img id="image"></div>

<!--thumbnails-->
<script type="text/javascript">
for (i=0; i<imageLn; i++)
{
var id=i;
document.write("<div id=\"div"+id+"\" onclick=\"display_image("+id+");\"><img id=\"thnail"+id+"\" src=\"\"></div>");
}
</script>

<!--select_set-->
<div id="tab1" onclick="display_set(1)">set 1</div>
<div id="tab2" onclick="display_set(2)">set 2</div>
<div id="tab3" onclick="display_set(3)">set 3</div>
```


**gallery.js**
```
var image=newArray();
image[0]=newArray("image1","1");
image[1]=newArray("image2","1");
image[2]=newArray("image3","2");
image[3]=newArray("image4","2");
image[4]=newArray("image5","3");
image[5]=newArray("image6","3");
var imageLn=image.length;
```

**gallery_css.js**
```
function add_css()
{
for (i=0; i<imageLn; i++)
{
addCSSRules("#div"+i+"{display:inline-block; cursor:pointer;}");
}

function addCSSRules(rules)
{
if (document.styleSheets)
{
if (document.styleSheets[0].addRule)
{
document.styleSheets[0].addRule(rules,null,0);
}
else 
{
document.styleSheets[0].insertRule(rules,0);
}
}
} 
```


**Additional references:**
[one]("http://www.hunlock.com/blogs/Totally_Pwn_CSS_with_Javascript")
[two]("http://www.webdeveloper.com/forum/archive/index.php/t-130717.html")
[three]("http://javascript.gakaa.com/stylesheet-insertrule-4-0-5-.aspx")

Thanks, as always, for the insights.

---

### Post by Dimarchi on 2012-05-24
Consider the following: id is a unique, single resource on a web page - there can not be more than one with the same id...class, on the other hand, is generic - there can be one or more. For your purposes, class is it. Define once, use many times, wherein with id you define once, and use once.

An example:

(in css...file, head, or inline)
```

.many {
 color: red;
}

<h2 class="many">One</h2>
<h2 class="many">Two</h2>
<h3 class="many">Three</h3>
<p class="many">Even more text</p>
```In all those cases the text would be red in colour, as dictated by the class definition.

```
#many {
 color: red;
}

<h1 id="many">Main subject</h1>
```Only one of #many is allowed, otherwise it would not be a unique identifier.

You could, of course, use both class and id together, for example:

```
.somethingGeneric {
 color: red;
}

#somethingUnique {
 font-size: larger;
}

<h4 class="somethingGeneric">One</h4>
<h4 class="somethingGeneric" id="somethingUnique">Two</h4>
<h4 class="somethingGeneric">Three</h4>
```In that example all h4 elements would have red text, but the one with an id would have text that is larger than the others.

There would be no need for things like div1, div2, div3, ...divn, etc. when you can do all that with a single .div1 (not going to call it div, since there is an element called div).

Should those images written with Javascript be the only images on the page, the css would be:

```
img{
 display: inline-block; /* css comment */
 cursor: pointer;
}
```Note: that means that all images (since it is referring to the element img) would have those features. With

```
img.someClass {
 display: inline-block;
 cursor: pointer;
}
```only image elements with a class of someClass would have those features. Plain

```
.someClass {
  display: inline-block;
  cursor: pointer;
}
```would mean that any element with a class of someClass would have those features.

Then there is a hierarchy to consider, if you wish to go that far...if you define the very same thing in file, head, and inline, the definition of head takes precedence over file, and inline takes precedence over head. Another example:

file.css is as follows:

```
.example {
 color: red;
}
```css in head element is as follows:
```

<head>
...
<style type="text/css">
.example {
 color: blue;
}
</style>
</head>
```and inline would be:
```

<p class="example" style="color: green;">example</p>
```Text colour should be green. Remove inline style attribute and text should be blue..and removing css in head should result in text being red.

Class and id can both serve as styling reference, even elements themselves can do that. Class is your infinite css, id is your single use css.

CSS 101. :)

---

