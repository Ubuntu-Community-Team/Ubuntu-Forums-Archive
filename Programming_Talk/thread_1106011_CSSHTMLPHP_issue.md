---
title: "CSS/HTML/PHP issue"
date: 2009-03-25
forum: Programming Talk
---

### Post by gjoellee on 2009-03-25
I am creating something I call a "hoverbox". It is the same thing as you can find on [www.crystalxp.net]("http://www.crystalxp.net") (the menu with some images below,  and when the cursor get's over it the information (the text above) changes).

However I have some problems. See how it looks on [www.kshoster.net]("http://www.kshoster.net") .
Don't worry about the text, I know how to fix that issue, but look at the images! They are shown in <ul><li> list that is supposed to go horizontal and without the "dots" in from of the icons!



I am not sure what is going wrong, so here is some files i think you might need to look at[B].

this in the hoverbox.css:[/B]
```
/* Hoverbox.css */
div#hoverContainer {
    width: 400px;
    height: 200px;
    margin: 0;
    padding: 0;
}
div#hoverContainer #textBox {
    width: 100%;
    height: 80%;
    padding: 2px;
}

div#hovercontainer #iconDock {
    width: 100%;
    height: 60px;
    background: url('img/bg.png');
}

div#hoverContainer #icondock ul {
    display: inline;
    width: 100%;
}

div#hoverContainer #icondock ul li {
    display: inline;
    width: 40px;
}
div#iconDock ul li a {
    padding-left: 48px;
    padding-bottom: 28px;
    padding-right: 10px;
}
div#iconDock ul li a:hover {
    padding-left: 48px;
    padding-bottom: 28px;
}

/*Special menu item images*/
div#iconDock ul li a#about {
    background: url('img/about.png') no-repeat;
}
div#iconDock ul li a#tux {
    background: url('img/tux.png') no-repeat;
}
div#iconDock ul li a#media {
    background: url('img/media.png') no-repeat;
}
div#iconDock ul li a#tipstricks {
    background: url('img/tipstricks.png') no-repeat;
}
div#iconDock ul li a#downloads {
    background: url('img/downloads.png') no-repeat;
}

/*Special menu item hover images*/
div#iconDock ul li a#about:hover {
    background: url('img/about_hover.png') no-repeat;
}
div#iconDock ul li a#tux:hover {
    background: url('img/tux_hover.png') no-repeat;
}
div#iconDock ul li a#media:hover {
    background: url('img/media_hover.png') no-repeat;
}
div#iconDock ul li a#tipstricks:hover {
    background: url('img/tipstricks_hover.png') no-repeat;
}
div#iconDock ul li a#downloads:hover {
    background: url('img/download_hover.png') no-repeat;
}
```this is the php file that makes the hoverbox appear:
```
<?php
$about = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/about.txt"));
$tux = nl2br(file_get_contents("./hoverbox/hoverbox/tux.txt"));
$media = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/media.txt"));
$tipstricks = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/tipstricks.txt"));
$downloads = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/downloads.txt"));
$default = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/default.txt"));
?>
<html>

<body>
    <div id="hoverContainer">
        <div id="textBox">
        <?php echo $default; ?>
        </div>
        <div id="iconDock">
            <ul id="vertical" title="Vertical">
                <li><a id="about" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $about; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="?c=about"></a></li>

                <li><a id="tux" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $tux; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/node/49"></a></li>

                <li><a id="media" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $media; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/node/4"></a></li>

                <li><a id="tipstricks" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $tipstricks; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/forum/3"></a></li>

                <li><a id="downloads" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $downloads; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/node/13"></a></li>

            </ul>
        </div>
    </div>
</body>
</html>
```

---

### Post by hastur on 2009-03-25
hi,

if you want to remove the list-item markers, take a look here :
[http://www.w3schools.com/css/css_reference.asp#list]("http://www.w3schools.com/css/css_reference.asp#list")
basically you should use "list-style:none" on the <ul> element.

concerning the fact that the icons overlap, I think it's because you're using background images, whose sizes aren't accounted for when calculating the layout of the list. if you used <img> element instead, the layout should expand to the height of the images, and you wouldn't have to create separate css entries for each menu...

I didn't understand clearly if you wanted your menu to be vertical or horizontal (like in the first site) but for horizontal you could use the float property...

---

### Post by gjoellee on 2009-03-25
> **hastur said:**
> hi,
I didn't understand clearly if you wanted your menu to be vertical or horizontal (like in the first site) but for horizontal you could use the float property...

I meant horizontal :)

---

### Post by hastur on 2009-03-25
well, to get an <ul> element to display horizontally, I usually "float" all <li> elements. of course this property as A LOT of drawbacks and shouldn't be used lightly (IMHO)...

---

### Post by bvanaerde on 2009-03-25
About the horizontal menu: most of it comes down to this:
```
/* Hoverbox.css */
#vertical li { display: inline; }

```
I suggest you give the <ul> tag another name though :p

edit: as hastur said: you can also use float:
```
/* Hoverbox.css */
#vertical li { float: left; }

```
There are some pros and cons with both methods. e.g. when using float, it's a bit more difficult to center the menu. When using display inline, it's difficult to give the list items a fixed width (all list items the same width).

---

### Post by gjoellee on 2009-03-25
I found a website, and I am using this to get it horizontal:
```
<style type="text/css">
#navlist li
{
display: inline;
list-style-type: none;
padding-right: 20px;
}
</style>
```It works great!

However, there is one final question.... the image img/bg.png is not showing! (Line is marked [COLOR=Red]RED[/COLOR])
[B]
here are the new updated files:[/B]
```
/* Hoverbox.css */

ul {
    list-style: none
} 
#navlist li
{
    display: inline;
    list-style-type: none;
padding-right: 0px;
}
div#hoverContainer {
    width: 400px;
    height: 140px;
    margin: 0;
    padding: 0;
}
div#hoverContainer #textBox {
    width: 100%;
    height: 80%;
    padding: 2px;
}

div#hovercontainer #iconDock {
    width: 100%;
    height: 100px;
   [COLOR=Red] background: url('img/bg.png');[/COLOR]
}

div#hoverContainer #icondock ul {
    display: inline;
    width: 100%;
}

div#hoverContainer #icondock ul li {
    display: inline;
    width: 40px;
}
div#iconDock ul li a {
    padding-left: 48px;
    padding-bottom: 28px;
    padding-right: 10px;
}
div#iconDock ul li a:hover {
    padding-left: 48px;
    padding-bottom: 28px;
}

/*Special menu item images*/
div#iconDock ul li a#about {
    background: url('img/about.png') no-repeat;
}
div#iconDock ul li a#tux {
    background: url('img/tux.png') no-repeat;
}
div#iconDock ul li a#media {
    background: url('img/media.png') no-repeat;
}
div#iconDock ul li a#tipstricks {
    background: url('img/tipstricks.png') no-repeat;
}
div#iconDock ul li a#downloads {
    background: url('img/downloads.png') no-repeat;
}

/*Special menu item hover images*/
div#iconDock ul li a#about:hover {
    background: url('img/about_hover.png') no-repeat;
}
div#iconDock ul li a#tux:hover {
    background: url('img/tux_hover.png') no-repeat;
}
div#iconDock ul li a#media:hover {
    background: url('img/media_hover.png') no-repeat;
}
div#iconDock ul li a#tipstricks:hover {
    background: url('img/tipstricks_hover.png') no-repeat;
}
div#iconDock ul li a#downloads:hover {
    background: url('img/download_hover.png') no-repeat;
}
``````
<style type="text/css">
#navlist li
{
display: inline;
list-style-type: none;
padding-right: 20px;
}
</style>

<?php
$about = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/about.txt"));
$tux = nl2br(file_get_contents("./hoverbox/hoverbox/tux.txt"));
$media = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/media.txt"));
$tipstricks = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/tipstricks.txt"));
$downloads = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/downloads.txt"));
$default = str_replace("\n", "", file_get_contents("./hoverbox/hoverbox/default.txt"));
?>
<html>
<head>
    <title>HoverBox by simz</title>
    <link rel="stylesheet" type="text/css" href="hoverbox/hoverbox.css" />
</head>
<body>
    <div id="hoverContainer">
        <div id="textBox">
        <?php echo $default; ?>
        </div>
        <div id="iconDock">
        <div id="navcontainer">
            <ul id="navlist">
            <li id="active"><a href="#" id="current">
                <li><a id="about" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $about; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="?c=about"></a></li>

                <li><a id="tux" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $tux; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="?c=tux"></a></li>

                <li><a id="media" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $media; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/node/4"></a></li>

                <li><a id="tipstricks" onMouseOver="document.getElementById('textBox').innerHTML = '<?php echo $tipstricks; ?>'" onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/forum/3"></a></li>


            </ul>
        </div>
        </div>
    </div>
</body>
</html>
```

---

### Post by gjoellee on 2009-03-26
[COLOR=Red]BUMP[/COLOR]eti[COLOR=Red]BUMP[/COLOR]

---

### Post by bvanaerde on 2009-03-27
I found out what's wrong... this is not good:
>             <ul id="navlist">
            <li id="active"><a href="#" id="current">
                <li><a id="about" onMouseOver="document.getElementById('textBox').**innerHTML = '<?php echo $about; ?>'"** onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="?c=about"></a></li>

                <li><a id="tux" onMouseOver="document.getElementById('textBox').**innerHTML = '<?php echo $tux; ?>'"** onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="?c=tux"></a></li>

                <li><a id="media" onMouseOver="document.getElementById('textBox').**innerHTML = '<?php echo $media; ?>'"** onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/node/4"></a></li>

                <li><a id="tipstricks" onMouseOver="document.getElementById('textBox').**innerHTML = '<?php echo $tipstricks; ?>'"** onMouseOut="document.getElementById('textBox').innerHTML = '<?php echo $default; ?>'" href="http://kshoster.net/forum/3"></a></li>


            </ul>
You are putting special characters( < and > ) inside the javascript, which confuses the CSS.
Those characters are inside $about, $tux, $media and $tipstrics (thus the textfiles you are using).

Result, this doesn't work:
> div#hovercontainer #iconDock { }
Because it can't find an element **iconDock** within **hovercontainer**.

The easy fix: replace
> div#hovercontainer #iconDock {
    width: 100%;
    height: 100px;
    background: url('img/bg.png');
}
with
> #iconDock {
    width: 100%;
    height: 100px;
    background: url('img/bg.png');
}

But I suggest you clean up the javascript. If I remember correctly, you can do this with the PHP function [htmlentities]("http://php.net/htmlentities").
Apply this function to $about, $tux, ... and you should be good to go.

---

### Post by gjoellee on 2009-03-30
Thanks...It totally works now! :P

---

