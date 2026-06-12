---
title: "[SOLVED] after update today, windows lost menu bars"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by nhasian on 2008-05-26
after applying the updates to Ubuntu 8.04 Hardy today, and rebooting, it seems I've lost the toolbar (maybe its called the titlebar) at the top of each window.  The one that allows you to minimize, maximize, make sticky windows, etc.  Theres not even an X to close the window.

There must be a setting somewhere i'm missing that turns that on or off...

I guess I'm lucky, I saw another post where a user didnt have any windows at all after applying the update and had to revert to a previous kernel.

---

### Post by philinux on 2008-05-26
Try this

sudo metacity --replace

After that if you running compiz you will have to turn on desktop effects and tick all the boxes again in compizconfig-settings-manager

---

### Post by nhasian on 2008-05-26
philinux, your a genius! how the heck did you know that?  that fixed the problem right away.  Now how do I mark this thread as resolved? :KS

> **philinux said:**
> Try this

sudo metacity --replace

After that if you running compiz you will have to turn on desktop effects and tick all the boxes again in compizconfig-settings-manager

---

### Post by philinux on 2008-05-26
Top of your post see Thread Tools pull down it's menu.

How do I know...

Broke fixed Broke Fixed Broke fixed .......

---

### Post by Happy_Man on 2008-05-26
You shouldn't need to stick a "sudo" in front of that, just ```
metacity --replace
``` should do just fine.

---

