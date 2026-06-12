---
title: "Search the Ubuntu Comunity..."
date: 2006-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by gasparov on 2006-01-27
Hi,
here you can find a few ways to add nicer searching capabilities to you browser,they are mostly for firefox

[IMG]http://www.koders.com/images/Firefox_Logo.gif[/IMG][SIZE="5"]**Firefox**[/SIZE]

at this moment there are 5 search plugins for firefox regarding ubuntu:
[LIST=1]
[*]Ubuntuforums
[*]UbuntuWiki
[*]UbuntuCustomizationGuide
[*]UbuntuPackages
[*]UbuntuBugs
[/LIST]

you can chose between 2 ways for installing:

[**Click and Add**]("http://gas.tranza.it/2006-ubuntu-search/"):--->*suggested* 

most common way,you click on the name of the search plugin and it get installed automagically, [you can do it here]("http://gas.tranza.it/2006-ubuntu-search/")

**Manual Install**

put the content of the attached gzip file in the searchplugin directory of your firefox profile.The path of the firefox profile is /home/user/.mozilla/firefox/xxxxx.yyy/
where user is your linux user,xxxx si a random number,yyy is your profile specific name,if you haven't changed is "default".
So you have to put them in something like this "home/gas/.mozilla/firefox/23oghrrg1n.default/searchplugins/"



[IMG]http://cookiecrook.com/img/browser_op7.gif[/IMG][SIZE="5"]**Opera**[/SIZE]: not tested

for opera you can use JonahRowley's tip @ [UbuntuForums]("http://www.ubuntuforums.org/showpost.php?p=156056&postcount=2")



[IMG]http://www.gnome.org/projects/epiphany/images/epiphany-64.png[/IMG][SIZE="5"]**Others/All**[/SIZE]: not tested

you can use ow50 tip @ [Ubuntuforums]("http://www.ubuntuforums.org/showpost.php?p=156071&postcount=4")


**To be Done**: nicer firefox search icons


have a nice Ubuntu Search

---

### Post by Puptentacle on 2006-01-27
BRILLIANT! Thanks a ton! And thanks to JonahRowley for the Opera tip.

---

### Post by traherom on 2006-01-28
Cool deal. :D

---

### Post by Heliode on 2006-01-28
Very good... just what I needed. Thanks!

---

### Post by ow50 on 2006-01-28
On Epiphany you can use [smart bookmarks](http://www.gnome.org/projects/epiphany/smartbookmarks.html).

Ubuntu Forums (this only prefills the form these days)
```
http://www.ubuntuforums.org/search.php?q=%s
```

Ubuntu Packages
```
http://packages.ubuntu.com/%s
```

---

### Post by Titus A Duxass on 2006-01-28
Very useful, thank you.

---

### Post by Micro Rotors on 2006-01-28
Now there is something I cant do without!

---

### Post by gasparov on 2006-01-30
[QUOTE=ow50]
Ubuntu Forums (this only prefills the form these days)
```
http://www.ubuntuforums.org/search.php?q=%s
```

Ubuntu Packages
```
http://packages.ubuntu.com/%s
```[/QUOTE]

Hi, 
   the plugin I made last year for ubuntuforums doesn't work anymore since they canched the forum so I had to change it,the search action has changed slightly
I had to change the code from this

```
<input name="q" user>
```

to this

```
<input name="do=process&query" user >
```

so for epiphany

```
http://www.ubuntuforums.org/search.php?do=process&query=%s
```

---

### Post by cutOff on 2006-01-30
Thanks a lot, it's very useful.

---

### Post by az on 2006-01-30
This is a thing that makes Ubuntu go Zoom!

Does the doc team know about this?

---

### Post by poofyhairguy on 2006-01-30
GREAT GUIDE!

Can I have permission to copy this and sticky it in the beginners forum?

---

### Post by gasparov on 2006-01-30
[QUOTE=poofyhairguy]GREAT GUIDE!

Can I have permission to copy this and sticky it in the beginners forum?[/QUOTE]

thanks,yes you can :mrgreen:

---

### Post by henriquemaia on 2006-01-31
Nice tip! This is really helpful.

Thanks a lot.

---

### Post by gasparov on 2006-02-04
Ubuntuforums Search is now on [mycroft.mozdev.org]("http://mycroft.mozdev.org/download.html?name=ubuntu&submitform=Search")

---

