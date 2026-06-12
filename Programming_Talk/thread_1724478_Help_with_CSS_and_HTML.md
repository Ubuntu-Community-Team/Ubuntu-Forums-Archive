---
title: "Help with CSS and HTML"
date: 2011-04-08
forum: Programming Talk
---

### Post by Nick-S on 2011-04-08
Greetings! 

I am having some issues with my page. Basically when you click and hold (or drag) on an image on the yellow area of my page  with your mouse, you will see a strange border stretching from the left  side of the page all the way to the image itself. The border should be  smaller. This also creates a clickable area on the page.  

I attached some screenshots and my page to show you what I mean.         

Your help will be greatly appreciated!

---

### Post by simeon87 on 2011-04-08
So what exactly have you done to find the cause of this? What are the relevant parts in the HTML and CSS? We can help but do you expect us to debug your problem?

---

### Post by Liverbones on 2011-04-08
The cause of the problem seems to be the relative positioning that you've applied for [FONT=Courier New]<img>[/FONT] tags within your [FONT=Courier New]<div>[/FONT] with the [FONT=Courier New]"img"[/FONT] class. The relative positioning pushes the element where you want it to go, visually... but not *technically*. The border around the image is caused by the link on the image being active. It's a visual cue to the user. Seeing as you pushed the images out of the way, that border is selecting from the top-left of the image's *original* position down to the bottom-right of its *current* position. Here's the relevant code:

[HTML]<div class="img">
<a href="ubuntu.html"><img src="ubuntu.gif" alt="ubuntu" title="ubuntu"></a>
<a href="fedora.html"><img src="fedora.jpg" alt="Fedora" title="fedora"></a>
<a href="debian.html"><img src="debian.gif" alt="debian" title="debian"></a>
<br>
<a href="opensuse.html"><img src="opensuse.png" alt="youtube" title="opensuse"></a>
<a href= "jolicloud.html"><img src="jolicloud.png" alt="jolicloud"title="jolicloud"></a>
<a href="reactos.html"><img src="reactos.png" alt="reactos" title="reactos"></a>
<br>
<a href="kubuntu.html"><img src="kubuntu.png" alt="kubuntu" title="kubuntu"></a>
<a href="mandriva.html"> <img src="mandriva.png" alt="mandriva" title="mandriva"></a>
<a href="arch-linux.html"><img src="arch.png" alt="arch linux"title="arch linux"></a>
<br>
<div>[/HTML]And in the CSS, these are the rules applied to the images:

```
.img img
{margin:10px; padding:20px; width: 85px; height:85px; position:relative; right:-390px; bottom:-150px;}
```

There were also quite a few typos in the code, resulting in some elements not being properly terminated, and I honestly have to wonder why you decided to use absolute and relative positioning on this page. There doesn't seem to be any need for it that I can see.

But in short, without redesigning the way the page is presented in the CSS, I don't see any easy way to remedy your problem with HTML and CSS alone, and using anything else would simply be complete overkill.

---

### Post by Nick-S on 2011-04-08
> **Liverbones said:**
> The cause of the problem seems to be the relative positioning that you've applied for [FONT=Courier New]<img>[/FONT] tags within your [FONT=Courier New]<div>[/FONT] with the [FONT=Courier New]"img"[/FONT] class. The relative positioning pushes the element where you want it to go, visually... but not *technically*. The border around the image is caused by the link on the image being active. It's a visual cue to the user. Seeing as you pushed the images out of the way, that border is selecting from the top-left of the image's *original* position down to the bottom-right of its *current* position. Here's the relevant code:

[HTML]<div class="img">
<a href="ubuntu.html"><img src="ubuntu.gif" alt="ubuntu" title="ubuntu"></a>
<a href="fedora.html"><img src="fedora.jpg" alt="Fedora" title="fedora"></a>
<a href="debian.html"><img src="debian.gif" alt="debian" title="debian"></a>
<br>
<a href="opensuse.html"><img src="opensuse.png" alt="youtube" title="opensuse"></a>
<a href= "jolicloud.html"><img src="jolicloud.png" alt="jolicloud"title="jolicloud"></a>
<a href="reactos.html"><img src="reactos.png" alt="reactos" title="reactos"></a>
<br>
<a href="kubuntu.html"><img src="kubuntu.png" alt="kubuntu" title="kubuntu"></a>
<a href="mandriva.html"> <img src="mandriva.png" alt="mandriva" title="mandriva"></a>
<a href="arch-linux.html"><img src="arch.png" alt="arch linux"title="arch linux"></a>
<br>
<div>[/HTML]And in the CSS, these are the rules applied to the images:

```
.img img
{margin:10px; padding:20px; width: 85px; height:85px; position:relative; right:-390px; bottom:-150px;}
```There were also quite a few typos in the code, resulting in some elements not being properly terminated, and I honestly have to wonder why you decided to use absolute and relative positioning on this page. There doesn't seem to be any need for it that I can see.

But in short, without redesigning the way the page is presented in the CSS, I don't see any easy way to remedy your problem with HTML and CSS alone, and using anything else would simply be complete overkill.


Should I use "float" instead of relative and absolute positioning?

I want the images to be side by side (as the screenshot above).
When I use "position:absolute;" the images stack on top of another.

What should I do?

---

### Post by dazman19 on 2011-04-08
don't use absolute. Absolute is generally only good for when you are using z-indexing. Other than that you generally want to refrain from using it. If the content is dynamic, e.g. each image was the output of a php or python loop, which acesses a database then you would want to design the page to cope with more or less objects.

Getting used to CSS is quite a frustrating process. Especially when you come to cross browser compatibility. Even I admit i am not much of a designer, more of a programmer/developer and my creative side is not that great. 

I would probably approach this by creating a <div> class to display each image, its caption and hyperlink etc. Then set the properties for that, and float them to the right/left of each other. Wrap them all in another content div.

---

### Post by Liverbones on 2011-04-08
Honestly, I'm not sure how to reply to that succinctly, so... I whipped up a different page using yours as a base that uses different methods (with no absolute or relative positioning) to get nearly the same result (with a couple of bonuses, actually: the content stays centered when resized, and the overflow isn't hidden).

Here's the code that I used:
[HTML]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
            "http://www.w3.org/TR/html4/loose.dtd">

<html>
<head>
    <title>Linux</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
<div class="header">
    <img src="linux.png" alt="linux">
    <h1>Welcome to the world of linux!</h1>
</div>
<div class="distros">
    <h2>Distros:</h2>
    <ul>
        <li><a href="distro.html">distro home</a></li>
        <li><a href="centos.html">centos</a></li>
        <li><a href="ubuntu.html">ubuntu</a></li>
        <li><a href="opensuse.html">opensuse</a></li>
        <li><a href="gentoo.html">gentoo</a></li>
        <li><a href="linux-mint.html">linux mint</a></li>
        <li><a href="fedora.html">fedora</a></li>
        <li><a href="red-hat.html">red hat</a></li>
        <li><a href="knopix.html">knopix</a></li>
        <li><a href="kubuntu.html">kubuntu</a></li>
        <li><a href="yellow-dog-linux.html">yellow dog linux</a></li>
        <li><a href="reactos.html">reactOS</a></li>
        <li><a href="mandriva.html">mandriva</a></li>
        <li><a href="jolicloud.html">jolicloud</a></li>
        <li><a href="debian.html">debian</a></li>
        <li><a href="arch-linux.html">arch linux</a></li>
    </ul>
</div>
<div class="img">
    <div>
        <a href="ubuntu.html"><img src="ubuntu.gif" alt="ubuntu"></a>
        <a href="fedora.html"><img src="fedora.jpg" alt="Fedora"></a>
        <a href="debian.html"><img src="debian.gif" alt="debian"></a>
        <a href="opensuse.html"><img src="opensuse.png" alt="opensuse"></a>
        <a href="jolicloud.html"><img src="jolicloud.png" alt="jolicloud"></a>
        <a href="reactos.html"><img src="reactos.png" alt="reactos"></a>
        <a href="kubuntu.html"><img src="kubuntu.png" alt="kubuntu"></a>
        <a href="mandriva.html"> <img src="mandriva.png" alt="mandriva"></a>
        <a href="arch-linux.html"><img src="arch.png" alt="arch linux"></a>
    </div>
</div>
<div class="footer">
    <a href="about.html">About </a> 
    <a href="home.html">Home </a>
    <a href="contact.html">Contact </a> 
    <a href="info.html">Information </a>
</div>
</body>
</html>
[/HTML]And here's the CSS style sheet:
```

a{text-decoration: none;}

.header {text-align: center;}
.header h1{font-size: 15pt;}
.header img {height:150px; width:180px;}

div.distros{background: red; float: left; padding: 0 10px 50px 10px; width: 270px;}
div.distros ul{background: pink; font-size: 12pt; list-style-type: none; margin: 0; padding: 0;}
div.distros h2{color: white; text-align: center;}

div.img{_padding-right: 270px; margin: auto; text-align: center;}
div.img img{border: 0; margin: 10px; padding: 20px; width: 85px; height: 85px;}
div.img div{background: yellow; width: 500px; margin: auto;}

div.footer {margin: 30px; padding: 20px; text-align: center;}
div.footer a{background: orange; font-size: 12pt; font-weight: bold; padding: 0 12px;}

```I recommend taking a look at how things are laid out in that source, and playing around with it some. I think you'll find that it's more accessible and easier to understand, at least generally. The only caveat in there is the [FONT=Courier New]_padding-right[/FONT] property used on [FONT=Courier New]div.img[/FONT], which is basically a CSS hack that only applies that property to IE 5.x or earlier.

If you have any questions about that, please feel free to let me know, either by replying to this post or by sending me a message. I'd be happy to help.

---

### Post by Nick-S on 2011-04-09
[COLOR=Black]**_bump_**[/COLOR]

---

### Post by Nick-S on 2011-04-11
bump

---

### Post by Nick-S on 2011-04-12
anyone?

---

### Post by Nick-S on 2011-04-12
Guys,  I need your help your please!

---

### Post by JacksSmith on 2011-04-13
The positioning of the image should be absolute in the web pages otherwise they will cause problems in layouts.

---

### Post by Nick-S on 2011-04-13
bump

---

### Post by Nick-S on 2011-04-14
Guys,  I need your help your please!

---

### Post by Nick-S on 2011-04-16
Guys,  I need your help your please!

---

