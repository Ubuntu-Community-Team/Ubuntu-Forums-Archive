---
title: "HTML/CSS - Would It Be Possible..."
date: 2009-04-04
forum: Programming Talk
---

### Post by matthewlowery on 2009-04-04
To code an Ubuntu taskbar? So that I could change the links, text images etc to suit my website's needs?

---

### Post by matthewlowery on 2009-04-04
exactly like the one [here]("http://theubuntuforums.org/")

---

### Post by Reiger on 2009-04-04
Yes: consider the clever use of CSS selectors triggered by an event on the parent element (code in white, because this forum has no spoilers):
```
[COLOR="White"]
<html><head><title>foo</title><style type="text/css">
li:hover { background: #aa5500; }
.short { max-width: 75%; }
.hid { display:none; }
ul:hover .hid { display:block;}
ul { max-width:200px; }
</style></head><body>
<ul>
<li class="short">Short</li>
<li class="hid">Hidden by default</li>
<li class="hid">Must move the mouse</li>
<li class="hid">To make this pop up.</li>
</ul>
</body></html>[/COLOR]
```

---

### Post by matthewlowery on 2009-04-04
that's vaguely helpful. Do I just steal the images and use the "idea" of your coding to make the toolbar? I'm not very good at CSS. HTML I'm only OK at too.

---

### Post by s.fox on 2009-04-04
Hi,

Yes it would be possible.  

One way is to take a look at the source code for the page.  You should be able to backward engineer it.  Don't forget to download all the necessary images, js and css files.   

Another way is to look at HTML menus that make use of Javascript and CSS.   [This]("http://dhtml-menu.com/") site has lots of different menus.  They provide good starting points.

-Ash R

---

### Post by matthewlowery on 2009-04-04
that probably would help if I could install it.

---

### Post by Reiger on 2009-04-04
> **matthewlowery said:**
> that's vaguely helpful. Do I just steal the images and use the "idea" of your coding to make the toolbar? I'm not very good at CSS. HTML I'm only OK at too.

Yup. I've added some refinements to the original which make the idea slightly clearer. It does about 95% of everything you need; you still have to:

(a) Do the styling your way (colour codes, images instead of (bullet) marks for li items, fonts etc.)
(b) Make it work with multiple menu's (positioning etc.)

None of that is terribly difficult, all of it is time consuming (Google really is among your best friends here, plenty of tutorials out there).

---

### Post by matthewlowery on 2009-04-04
I've noticed a problem with it. If I highlight anywhere over the line, it opens the list. But is there a way I can make it only open on hovering over the actual word/image?

---

### Post by Reiger on 2009-04-04
> **matthewlowery said:**
> I've noticed a problem with it. If I highlight anywhere over the line, it opens the list. But is there a way I can make it only open on hovering over the actual word/image?

Change:

```

.short { max-width: 75; }

```

To:
```

.short { max-width: 75%; display:inline; }

```

---

### Post by matthewlowery on 2009-04-04
okay you must think I'm a complete noob by now, but can I make the drop down stuff horizontal?I mean:

|Home|Tutorials|
|####|
|####|

or just tutorials?
So when I hover over home, it drops down with the links and when I hover over tutorials that drops down
I'll show you what code I have right now.
```


<html><head><title>foo</title><style type="text/css">
li:hover { background: #aa5500; }
.short { max-width: 75%; display:inline; }
.hid { display:none; }
ul:hover .hid { display:block;}
ul { max-width:200px; }
</style></head><body>
<table border="0">
<tr>
<td><ul>
<center><li class="short"><img src="home.png">   <a href="index.html">Home</a></li>
<li class="hid"><img src="chat.png">   Chat</li>
</ul></td>
<td>
<ul>
<li class="short"><img src="tutorials.png">   Other</li>
<li class="hid"><img src="forums.png">   Forums</li>
<li class="hid"></li>
<li class="hid"></li>
</ul></td></center>
</tr>
</table> 
</body></html>
```

Also, when i hoveer over Home or Other, it moves the other one down a bit.

---

### Post by s.fox on 2009-04-04
Use CSS.  Look at the position attibute. I have included a solution to your problem as a spoiler.


Spolier

```
[COLOR=White]<html><head><title>foo</title>

<style type="text/css">
li:hover { 
background: #aa5500; 
}

.short { 
max-width: 75%;
display:inline; 

}

.hid {
display:none;
}

ul:hover .hid {
display:block;
position: fixed;
}

ul {
max-width:200px; 
left:5px;
top:5px;
}

</style></head><body>
<table border="0">
<tr>
<td><ul>
<center><li class="short"><img src="http://theubuntuforums.org/images/theubuntuforums/off.gif">   <a href="index.html">Home</a></li>
<li class="hid"><img src="http://theubuntuforums.org/awmdata/menu1/chat.png">   Chat</li>
</ul></td>
<td>
<ul>
<li class="short"><img src="http://ubuntuforums.org/images/misc/im_msn.gif">   Other</li>
<li class="hid"><img src="http://theubuntuforums.org/awmdata/menu1/sent.png">   Forums</li>
<li class="hid"></li>
<li class="hid"></li>
</ul></td></center>
</tr>
</table> 
</body></html>


[/COLOR]

```

---

### Post by matthewlowery on 2009-04-04
thanks. How would I add a background image to the things, and change the background image when it's hovered over like on [http://www.theubuntuforums.org/](http://www.theubuntuforums.org/)   ?

---

### Post by s.fox on 2009-04-04
Take a look [here]("http://www.hypergurl.com/rolloverimage.html") for ideas.  Its a javascript mouseover event.

---

### Post by matthewlowery on 2009-04-04
too confusing for me all of this. I don't have any money to give you (i'm 13 and my parents don't trust me etc etc) but could you code it for me? I'd give credit and if this forum has it, I'd give you rep?

---

### Post by s.fox on 2009-04-04
Hi,

Where exactly are the images you want to use?  URL links would be helpful

---

### Post by matthewlowery on 2009-04-04
well if you right click on the forum and click Page Info you get all the images.
For the Home etc, you decide what's best. As for backgrounds/hover image, use the same.
Thanks for this!
EDIT: I'm not entirely sure, but I'll just give you all of the ones I think shall I?
[http://theubuntuforums.org/awmdata/time/gnome-panel-button.png](http://theubuntuforums.org/awmdata/time/gnome-panel-button.png)
[http://theubuntuforums.org/awmdata/time/dropdown-bg-rollover.png](http://theubuntuforums.org/awmdata/time/dropdown-bg-rollover.png)
[http://theubuntuforums.org/awmdata/time/dropdown-right-rollover.png](http://theubuntuforums.org/awmdata/time/dropdown-right-rollover.png)
[http://theubuntuforums.org/awmdata/time/dropdown-left-rollover.png](http://theubuntuforums.org/awmdata/time/dropdown-left-rollover.png)
[http://theubuntuforums.org/awmdata/menu1/gnome-panel-button.png](http://theubuntuforums.org/awmdata/menu1/gnome-panel-button.png)
[http://theubuntuforums.org/awmdata/menu1/gnome-panel-button-bg-rollover.png](http://theubuntuforums.org/awmdata/menu1/gnome-panel-button-bg-rollover.png)

---

### Post by s.fox on 2009-04-04
I am now confused.   Which image do you want to change when the user hovers over it?   The ones on the site you saw only have a single image that changes when the user hovers over it (the power button)

EDIT:  Do you just want the background grey panel?

---

### Post by matthewlowery on 2009-04-04
I'm not entirely sure. The normal background is grey as you can see, and then you hover over it and it goes orange. if you have firefox, right click anywhere on the page and click Page Info. Then go to Media, it has all the scripts and images used on that page.

---

### Post by matthewlowery on 2009-04-04
> **Ash R said:**
> I am now confused.   Which image do you want to change when the user hovers over it?   The ones on the site you saw only have a single image that changes when the user hovers over it (the power button)

EDIT:  Do you just want the background grey panel?

yes please, with the orange hover. Just include some default text links and chat images etc.
THANKS AGAIN:guitar:

---

### Post by s.fox on 2009-04-04
I have some other matters that require my attention.  I have more or less done what you asked for.  There is a slight alignment issue with the text overlapping the panel.  I shall leave you to figure out.    I will give you a hint.  You need to do something with CSS.

```
[COLOR=White]<html>
<head>
<title>foo</title>
<style type="text/css">

li:hover { 
background: #FFB13D; 
}

.short { 
max-width: 10%;
display:inline;

}

.hid {
display:none;
}

ul:hover .hid {
display:block;
position: fixed;
}

ul {
max-width:100px; 
left:5px;
top:4px;
}

.gnomepanel {
background-image: url('http://theubuntuforums.org/gnome-panel.png');
background-repeat: repeat-x;
}
</style>
</head>



<body>
<div class ="gnomepanel">
<table border="0">
<tr>
<td><ul>
<center><li class="short"><img src="http://theubuntuforums.org/awmdata/menu1/go-home.png">  Home</li>
<li class="hid"><img src="http://theubuntuforums.org/awmdata/menu1/chat.png">  Chat</li>
</ul></td>
<td>
<ul>
<li class="short"><img src="http://theubuntuforums.org/awmdata/menu1/text-editor.png">  Other</li>
<li class="hid"><img src="http://theubuntuforums.org/awmdata/menu1/insert-image.png">   Forums</li>
<li class="hid"></li>
<li class="hid"></li>
</ul></td></center>
</tr>
</table> 
</div>
</body></html>[/COLOR]          

```

---

### Post by matthewlowery on 2009-04-04
thanks. LOL IF ONLY IT COULD HAVE BEEN A HTML ISSUE!! I'll prob just ask on Yahoo Ansers or something. I know nothing about CSS...

---

### Post by s.fox on 2009-04-04
[Here]("http://www.w3schools.com/css/") is a good place to start learning CSS.   W3schools is pretty good place for tutorials anyway.  I would also suggest you learn more about JS and HTML. :D

Good luck with your site.

P.S.  What is the link to your site anyway?

---

### Post by matthewlowery on 2009-04-04
it's not hosted yet. But my school has a website that they can create all sorts of subdomains and stuff. HTML I'm good with, CSS not very good. Thought about trying JS though. I have no idea what to do with the alignment :S

---

### Post by s.fox on 2009-04-04
Hmm...

It seems I forgot to give the drop down items a grey background aswell.  ;)

---

### Post by matthewlowery on 2009-04-04
that's just mean :(

---

### Post by s.fox on 2009-04-04
What would happen if you took the images tags out?  Think why did it do that?

---

### Post by matthewlowery on 2009-04-04
by image tags do you mean <img src="">? If you remove the img tags then it doesn't know what to look for.

---

### Post by s.fox on 2009-04-04
No,  **TOTALLY** remove the img tag and you will see what I am getting at.

---

### Post by matthewlowery on 2009-04-05
if you totally removed it, you would just have a text wouldn't you?

---

### Post by s.fox on 2009-04-05
> **matthewlowery said:**
> if you totally removed it, you would just have a text wouldn't you?

Yes,  but what else happened?  Try it.  It might give you some ideas.

---

### Post by fiddler616 on 2009-04-06
If you finish it, and decide to release it under the GPL or similar, would you please let me know? Thanks.

---

### Post by matthewlowery on 2009-04-10
> **Ash R said:**
> Yes,  but what else happened?  Try it.  It might give you some ideas.

well all the text was inside the bar.

---

### Post by fiddler616 on 2009-04-10
> **Ash R said:**
> Hmm...

It seems I forgot to give the drop down items a grey background aswell.  ;)
I have never studied CSS in my life, but using a mixture of logic and luck, I came up with the following:
```
[COLOR="White"].hid {
	display:none;
	background-image: url('http://theubuntuforums.org/gnome-panel.png');
	background-repeat: repeat-x;
}[/COLOR]
```
I don't know if that's how it's supposed to be done, but it works.

---

### Post by Joeb454 on 2009-04-10
Is that meant to be white text? :)

---

### Post by fiddler616 on 2009-04-10
> **Joeb454 said:**
> Is that meant to be white text? :)
Unfortunately, yes. I really don't like white text, but I wanted to be in the same style as previous code entries in this thread.

---

### Post by fiddler616 on 2009-04-10
My current headache: 
If I have position:fixed; in ul:hover .hid, all of the submenu entries that appear are on top of each other. If I remove the position:fixed;, the entries stack nicely, but the other menu titles move down a line or two, until I stop hovering.
I tried moving position:fixed; to .short, except that just made the menu titles appear on top of each other.

---

### Post by fiddler616 on 2009-04-10
(Deleted)

---

