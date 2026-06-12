---
title: "[SOLVED] Awn?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-07-30
I see people have the Apple looking bar on their desktops. I downloaded some time time ago. How do I make it stay up all the time. I have tried messing around with it, and it only seems to want to work as a window open screenlet. It only shows what the applications which I have open.
I would like to get rid of my panels if I could, is that possible with this?

---

### Post by Potatoj316 on 2008-07-30
yeah, its possible.  Try right clicking on it and choosing properties to change how it appears

---

### Post by Andrew79 on 2008-07-30
alright, how about this. let me rephase my question. can someone tell me step by step the EASIEST way to make the awn work. Please tell me a simple way to install it and set it up.

---

### Post by Potatoj316 on 2008-07-30
to install
```
sudo aptitude install avant-window-navigator
```
(there may be some spelling errors there, i think you can figure it out)

to run
```
avant-window-navigator
```
(again check for spelling, you can probably just type ava[tab] where [tab] is the tab key)

Umm, not to sound rude or anything but have you even tried?  I can understand you might have trouble installing, it is different than windows, but configuring it?  Just play around for a few minutes and ask a more specific question.

---

### Post by billgoldberg on 2008-07-30
The AWN version in the ubuntu repositories is severly lacking features.

Download it from their website.

Or better, download cairo-dock, it better than awn and has better themes.

---

### Post by Andrew79 on 2008-07-30
okay, so I have tried all these items. i installed compiz. i have in my applications menu and in the system menu a place to click for the program. all that happens is the screen flashes, and nothing! I have tried a bunch of stuff here, and something is missing, but i have no clue what.
and the whole cairo dock thing, went to the site an have no clue what they are going on about to install it. and it is in FRENCH!

---

### Post by Potatoj316 on 2008-07-30
try this
```
sudo aptitude install compizconfig-settings-manager
```then it should show up in system->prefrences as like the 3rd item.

---

### Post by Andrew79 on 2008-07-30
okay, what i figured out on my own is that you have to have the visual effects setting NOT on basic.  
now, if someone could please explain how to clean the dock up. now that i have it up and running, it is very messy. i have the gentoon icons running, but it shows in the task part of the dock the original icon. and in the backround of the dock is shadows of running programs? why is this so messy looking?

---

### Post by fabounet on 2008-07-31
> in the backround of the dock is shadows of running programs
means ?

applications icons are provided by X directly, except if you ticked the option "overwrite X icons".

---

### Post by gettinoriginal on 2008-07-31
I know you have it marked as solved, but my bookmarked pages to check for things like this are:

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

[http://www.gnome-look.org/](http://www.gnome-look.org/)

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by tjwoosta on 2008-07-31
> Or better, download cairo-dock, it better than awn and has better themes. 

i have to disagree

(i have actually compared cairo and awn side by side)

no matter what theme you pick with cairo dock it still looks too tall and unrealistic like  

with AWN it can look exactly like the mac leopard dock

there are only two downsides about AWN 

1. you cant have it positoned at the top or sides of the screen

2. if you choose the zoom effect for icons it will look kinda distorted (but i like the squish effect better anyway)

---

### Post by nkri on 2008-07-31
The easiest way to get AWN to work?  Get Cairo-dock.  Add this to your sources.lst:
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

Cairo-dock is a lot more flexible, has better applets, looks nicer, and works very well with Compiz.  AWN has none of this (in my opinion).

---

