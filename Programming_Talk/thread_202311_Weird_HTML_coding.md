---
title: "Weird HTML coding??"
date: 2006-06-23
forum: Programming Talk
---

### Post by hagen00 on 2006-06-23
Hi there

We're working together with a graphic designer that wants us to add some PHP to his static website. 

When got his pages, I saw, to my suprise, that every reference he makes to either images or stylesheets or whatnot, are preceeded by a /. For example, an image would be referenced like <img src="/images/logo.gif">, eventhough to my mind, it should be <img src="images/logo.gif"> because I'm in the root folder, looking to go up one. And sure enough, his code doesn't work on my localhost, only when i strip the first slash. 

I'm developing on windows, but our servers are linux. The way he's done it works on neither. What's going on here? Is there some setting in apache that I need to change to make it work with the / in front? It must have worked for him, but obviously the way our servers are set up, it doesn't.

I really don't want to go through all his pages and remove the leading slash. 

Any ideas? Thanks!

H

---

### Post by dabear on 2006-06-23
you see, if you develop locally, you probably would use a URL like this: [http://localhost/myprojet/index.php](http://localhost/myprojet/index.php) , while the project - when uploaded - is located on htp://yourCite.ext/index.php

Now /img/myImg.png would be a reference to a folder inside "the root folder" of the URL. Because the finished project would be located in a root folder, but not when you are developing locally, the URL would become wrong only when developing locally.

[http://localhost/myprojet/index.php](http://localhost/myprojet/index.php) + /img/myImg.png would give you [http://localhost/img/myImg.png](http://localhost/img/myImg.png) and _not_ [http://localhost/](http://localhost/)**myprojet**/img/myImg.png

using relative (to the current folder, not the root folder) URL's will offcourse solve your problem.

---

### Post by hagen00 on 2006-06-23
Thanks bjoern - I'm assuming that might be your name :)

Ja, I figured that's what's happening. But I wonder how the graphic designer developed. He couldn't have dumped everything into his root folder...anyway. My solution is to find and delete "/ 

Cheers

H

---

### Post by dabear on 2006-06-23
[quote=hagen00]Thanks bjoern - I'm assuming that might be your name :)
[/quote] Good guess, Bjørn actually (bjørn, not bjoern or björn)

> 
Ja, I figured that's what's happening. But I wonder how the graphic designer developed. He couldn't have dumped everything into his root folder...anyway. My solution is to find and delete "/ 

You're German? 

I believe it would be better to use some sortof includescript from the serverside, that way you don't have to do the menus/links by hand, and the path would be correct even if your site is located on a different server

---

