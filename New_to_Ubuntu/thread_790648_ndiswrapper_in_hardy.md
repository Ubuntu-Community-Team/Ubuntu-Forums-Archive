---
title: "ndiswrapper in hardy"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by bm13084 on 2008-05-11
the instructions ive been finding only refer to gutsy and earlier... where can i  find the new ndiswrapper files?

---

### Post by oarion7 on 2008-05-11
As I recall, use the same method for Gutsy, and then follow the directions here:

(EDIT) link removed

There may be another way to do it, actually, but I believe that's the route I took. For Heron it works exactly the same as Gutsy, only there is a conflict in Heron's included drivers with ndiswrapper that a little scripting (see the link) can work around just fine.

That particular method was used for the Hardy beta rather than the final version, but I believe that's still the method to use.


***EDIT***

No. Here's what you want:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The methods for installing on Hardy Heron are exactly the same as Gutsy, except for the additional steps. Scroll down to the section called "Hardy Bug Fix" which gives you the scripts to use. Basically you need to rig Hardy so that on start up it disables the other drivers, enables ndiswrapper first, and then re-enables the other ones. Or something like that. Check it out, worked for me. :)

---

