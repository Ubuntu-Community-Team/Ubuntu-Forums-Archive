---
title: "Got a couple of bugs to confirm..."
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-06
1.) [Notification bubbles in Unity 2D don't get transparent enough on mouse-over.]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/821719") **CONFIRMED**
2.) [Launcher icons for Applications and Places lenses not transparency-compatible.]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/821989") **CONFIRMED**
3.) [Shadows of Ubuntu button and top panel not equal (only an issue with transparent launcher background).]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/821991") **CONFIRMED**
4.) [Term inconsistency in CCSM's grid plugin: "upper" vs. "top".]("https://bugs.launchpad.net/ubuntu/+source/compiz-plugins-main/+bug/821998")
5.) ["Failed to load image ... Icon has zero width" error from Nux in .xsession-errors.]("https://bugs.launchpad.net/ubuntu/+source/nux/+bug/822002") **CONFIRMED**

Go, confirm! NOW!

---

### Post by lucazade on 2011-08-07
about 2nd I believe lenses are going to be added to ubuntu button quicklist, directly in the launcher.

[https://code.launchpad.net/~agateau/unity-2d/move-bfb-to-launcher/+merge/69677](https://code.launchpad.net/~agateau/unity-2d/move-bfb-to-launcher/+merge/69677)

.. Item quicklist should contain a list of available Dash lenses..

---

### Post by MacUntu on 2011-08-07
So the BFB will become a big launcher item? Will it replace the Ubuntu button or just be another fixed launcher item (= bad for those poor guys with netbooks).

Anyways, it can only get better, because right now those two links to the lenses are at the bottom of the launcher, which means that they don't really allow "quick access" in case you got a lot of launcher items.

---

### Post by lucazade on 2011-08-07
> **MacUntu said:**
> So the BFB will become a big launcher item? Will it replace the Ubuntu button or just be another fixed launcher item (= bad for those poor guys with netbooks).

Anyways, it can only get better, because right now those two links to the lenses are at the bottom of the launcher, which means that they don't really allow "quick access" in case you got a lot of launcher items.

Yes, BFB is becoming a big launcher item and will replace the classical button on the panel, and lenses will be activated from quicklist on right click.
(at least this is what I understood!)

In this screenshot BFB is present on both panel and launcher, maybe WIP
[IMG]http://www.oneopensource.it/files/2011/08/Screenshot-at-2011-08-04-123907-e1312454701641.png[/IMG]

---

### Post by MacUntu on 2011-08-07
The question is - what will be put in the space of the current BFB? 

Will it become part of the launcher? In that case I wonder if the Ubuntu item's quicklist wouldn't either cover the top panel (would look weird), or show the quicklist with a little offset to not cover the top panel (again, would look weird).

Will it not become part of the launcher?  In that case I wonder if it would be left unused (would look weird too), get the window buttons moved there (doubt that, given that that would put the close button in the corner), or maybe some other functionality?

Let's see where this is going. :)

---

### Post by MacUntu on 2011-08-09
Does anyone care to confirm the last unconfirmed bug? :)

---

### Post by mc4man on 2011-08-09
> **MacUntu said:**
> Does anyone care to confirm the last unconfirmed bug? :)

The description is slightly off but as it is in grid seems ok and consistent
(the action takes place in the upper left corner, the window is placed in that ex. from the top left corner, those aren't the same places

---

### Post by MacUntu on 2011-08-10
I disagree.

If it's "Upper Left Corner" for the action "top_left_corner_action" and "Bottom Left Corner" for the "bottom_left_corner_action" then that's definitely not consistent.

---

### Post by mc4man on 2011-08-10
I guess ? I'm not looking at what the tooltip describes - so the 
Resize Action(s) Upper Left Corner & Upper Right Corner make sense, that's where the action takes place vs. where the window could be set if desired - Top ...

But from that viewpoint the displayed Resize Action for Bottom .. could be something else that described the action point vs. a possible setting point like Lower ..
which seems a bit silly so perhaps you're correct..

---

### Post by MacUntu on 2011-08-10
Besides, you can still use Compiz without an upper panel, so the action WOULD take place at the top. :P

I know... it's nitpicking, but to me it's those small things that count. :)

BTW: I'm still getting all Monk about the different colors in the ubuntu-mono icon set: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/620041](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/620041)

:D

---

### Post by lucazade on 2011-08-10
> **MacUntu said:**
> Besides, you can still use Compiz without an upper panel, so the action WOULD take place at the top. :P

I know... it's nitpicking, but to me it's those small things that count. :)

BTW: I'm still getting all Monk about the different colors in the ubuntu-mono icon set: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/620041](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/620041)

:D

confirmed ubuntu-mono-icon bug report..
agree with you.. evil is in the details! ;)

---

### Post by Sashin on 2011-08-11
I think the BFB should really stand out from the launcher to make it more obvious that its not just another app. Also I like how before you could invoke the launcher by going to the top left corner, but now it requires a bit of aiming.

This is an idea to try and remedy that issue, what do you guys think of this mockup?

[http://i55.tinypic.com/2ezh2d2.jpg](http://i55.tinypic.com/2ezh2d2.jpg)

(I know its poorly drawn, but basically it means the BFB is fundamentally different from launcher icons and can still be invoked from top corner.)

---

### Post by petersonja on 2011-08-17
Hi all!

I've got three bugs to confirm. I tried to search on Launchpad, but no luck.

First:

If i click to the shutdown menu (or what is the name of it) I've got only an empty menu.

Second:

If I click the Banshee application in Sound Menu, the menu isn't close, so first I think I didn't click to it.

Third:

My voulme slider it at top, but it isn't fill the slider. 

Sorry for bad english

---

### Post by MacUntu on 2011-08-17
The third one is a known bug (if you mean that the slider doesn't work right), the second I can confirm, but I don't get the first one.

---

