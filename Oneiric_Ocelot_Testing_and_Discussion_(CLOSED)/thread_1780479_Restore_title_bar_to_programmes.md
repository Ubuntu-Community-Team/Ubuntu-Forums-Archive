---
title: "Restore title bar to programmes"
date: 2011-06-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nzjethro on 2011-06-12
Hi guys, thought I'd have a blat on Oneiric! Probably a silly question, but how do I restore the title bar (i.e. the close, maximise, minimise, and title etc., don't know what it's propper name is) to the programmes rather than the top panel? I've looked around and tried a couple of tips, but nothing's worked. Anybody got any hints for me?

---

### Post by mc4man on 2011-06-12
To remove entirely just remove the appmenu-gtk3 and for qt app's the appmenu-qt packages
firefox uses an extension, disable or remove

You can also disable or enable both in app and global on an individual basis by editing the apps .desktop or diverting the binary if cli use is also important

---

### Post by dino99 on 2011-06-12
depend on what you want to restore, into a terminal, run either:

unity --reset
unity --replace
metacity --replace
gnome-panel --replace

note: choose it to agree with your login choice indeed

---

### Post by jerrylamos on 2011-06-12
From a netbook view, this one, Oneiric Ocelot seems to do a better job of conserving lines than gnome panel does.  That leaves more lines available for my applications and the browser.

Yes, I do hunt around for "edit - copy" sometimes which is disconnected from the window I'm copying from, but it works.

Now on a couple of my test pc's with bigger screens it's not as much concern because of space, but it does reduce the clutter.

Wonder what's coming next...

Jerry

p.s.  I'm not into tablets.  This nicely responsive $249 1GB 250 GB netbook is far more to my preferences than the "cave man ugh me point" smearing fingerprints all over the screen.

---

### Post by nzjethro on 2011-06-12
Cheers for the replies all.

> **mc4man said:**
> To remove entirely just remove the appmenu-gtk3 and for qt app's the appmenu-qt packages


Tried that, but I'll give it another go.

> unity --reset
unity --replace
metacity --replace
gnome-panel --replace

Haven't tried that. I'm on my Maverick session at the mo, but when I flick back to Oneiric I'll run those.

> From a netbook view, this one, Oneiric Ocelot seems to do a better job of conserving lines than gnome panel does. That leaves more lines available for my applications and the browser.


Mmm, I've got a 15 inch laptop screen, so not heaps of screen space to spare, but enough that I'm keen to remove this feature. Too Mac-like for my liking. Mag has done a lot to make OSX look good, but in my opinion a global menu in the panel is not one of them.

---

### Post by cariboo on 2011-06-12
If you don't like the global menu, Id suggest trying a different Ubuntu version, I've heard good things about Lubuntu, Xubuntu and Kubuntu.

---

### Post by kansasnoob on 2011-06-12
> **cariboo907 said:**
> If you don't like the global menu, Id suggest trying a different Ubuntu version, I've heard good things about Lubuntu, Xubuntu and Kubuntu.

+1!

With the advent of gnome-panel-3 those seeking a more "retro" DE are much better off looking beyond Gnome.

I'd also point out though that 10.04/Lucid is still supported until April 2013 :D

No need for panic, much time to transition ;)

---

### Post by mc4man on 2011-06-12
> Tried that, but I'll give it another go.

Sorry - I misunderstood you - thought you meant the global menu itself - 
I'm not sure there is any easy way to keep the title bar with the app window when it is maximized other than not to maximize them fully

---

### Post by nzjethro on 2011-06-12
> If you don't like the global menu, Id suggest trying a different Ubuntu version, I've heard good things about Lubuntu, Xubuntu and Kubuntu.


Cool, I'm using Maverick with XFCE as my primary OS at the moment, and very much enjoying it. Tried KDE with Ubuntu but bleh, and haven't dabbled with lubuntu.

But I figured I'd give Oneiric a blat out of the box Unity and all while testing it, hence trying  to make it look more XFCE-ey.

---

