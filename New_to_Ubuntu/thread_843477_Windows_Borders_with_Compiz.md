---
title: "Windows Borders with Compiz"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by shanepardue on 2008-06-28
I've noticed with the latest Nvidia driver and Compiz that my window 
decoration flickers this annoying white bar across half of the bar. Here's 
a screenshot..

[http://img.photobucket.com/albums/v330/shanepardue/screenshot1-4.png](http://img.photobucket.com/albums/v330/shanepardue/screenshot1-4.png)

I've reverted Nvidia drivers and the problem seems to go away, but the 
framerates aren't as good on that driver. Also, with metacity the problem 
ceases to occur.

Any help is greatly appreciated!

---

### Post by defrex on 2008-06-28
Ya, I have similar render issues with the latest nvidia drivers. I don't think there is a solution other then patience. Just use the drivers from the restricted driver manager and hope they fix the problem sooner then later.

---

### Post by shanepardue on 2008-07-08
Nvidia update today to no avail

---

### Post by ZabiGG on 2008-07-08
I had the same problems when I was running Emerald as the window decorator. I switched to gtk (which can also do nice stuff if you're willing to fiddle with gconf-editor) while still using compiz for the rest, and my border problems were solved.

Hope this helps,

Z.

---

### Post by shanepardue on 2008-07-09
> **ZabiGG said:**
> I had the same problems when I was running Emerald as the window decorator. I switched to gtk (which can also do nice stuff if you're willing to fiddle with gconf-editor) while still using compiz for the rest, and my border problems were solved.

Hope this helps,

Z.
I don't have Emerald installed..Thanks for the tip though!

---

### Post by tjwoosta on 2008-07-09
THAT GIVES ME AN IDEA

maybe using emerald to draw the window boarders (rather then  compiz) would actually solve your problem

its worth a try anyway

first install emerald theme manager from synaptic
or 
```
sudo apt-get install emerald
```

then find a good emerald theme from gnome-look.org (under beryl)

then import the theme into emerald  (system-preferences-emerald theme manager)

then press alt-f2 and type emerald --replace in the box   (its important to use alt-f2 rather then the terminal)

if it works and fixes your window boarders then you can set it to activate at every login 

go to system-preferences-sessions  (click add and put emerald --replace in the box that says command)

---

### Post by shanepardue on 2008-07-09
> **tjwoosta said:**
> THAT GIVES ME AN IDEA

maybe using emerald to draw the window boarders (rather then  compiz) would actually solve your problem

its worth a try anyway

first install emerald theme manager from synaptic
or 
```
sudo apt-get install emerald
```

then find a good emerald theme from gnome-look.org (under beryl)

then import the theme into emerald  (system-preferences-emerald theme manager)

then press alt-f2 and type emerald --replace in the box   (its important to use alt-f2 rather then the terminal)

if it works and fixes your window boarders then you can set it to activate at every login 

go to system-preferences-sessions  (click add and put emerald --replace in the box that says command)
That is one workaround..I imagine if this bothers me enough, I'll switch to Emerald. Thanks for posting this on the thread!

---

### Post by aan0213 on 2008-12-26
found something intersting...
i used to had the same problem with compiz enabled + latest nvidia driver..
metacity window decorator always flickering, and this bug toke all my time, and then after googling, found something 

i decide to downgrade nvidia driver to version 96, and then after that i uninstall the driver, and again, reinstall the latest nvidia driver version 177.80... miracle happpens> the bug is gone

metacity window decorator isn`t flickering anymore..
this trick works for me, and hopely.. for anyone who has the same problem..
n_n

best regards, Indonesian...

---

