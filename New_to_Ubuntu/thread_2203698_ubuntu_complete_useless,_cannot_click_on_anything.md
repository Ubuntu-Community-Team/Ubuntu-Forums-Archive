---
title: "ubuntu complete useless, cannot click on anything"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by tijn2 on 2014-02-04
good evening from the netherlands,
i am a complete newbe regarding to linux, 
i can remember i used ubuntu once moor a couple of years ago. now i wanted to try it again.

but i have a problem that makes ubuntu completely useless to me.

i have installed ubuntu 12.04 on my laptop succesfully, when i boot the computer he boots completely but i cannot click on anything.

the mouse cursor moves but i cannot click anything. nothing responds.

also the resolution isn't correct so dat i cannot see the buttons on the left properly.

but since i cannot click on anything its impossible for me to change that.
does anybody have a solution?
regards
Tijn

---

### Post by Iowan on 2014-02-04
Does CTRL-ALT-F2 take you to a terminal?
(CTRL-ALT-F7 should take you back to desktop)

---

### Post by tijn2 on 2014-02-04
when i press ctr+alt+f2 i get a black screen with some text i cannot completely read, because of the resolution, but it says something about help.ubuntu.com and ubuntu:"$

when i press ctrl+alt+f7 my mouse cursor appears, but the text stays the same, so no desktop.

---

### Post by grahammechanical on 2014-02-04
My suggestion would be to select Recovery Mode from the Grub boot menu and then select Resume. If that gets you to a desktop open Additional Drivers and change video drivers. I use the Nouveau open source video driver. It works fine for me.

Did you test Ubuntu using a live session? How well did it work? You were using Nouveau during the live session. When we install and tick to install third party software we also get a proprietary video driver.

Regards.

---

