---
title: "drag &amp; drop files  folders with Ubuntu"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by thelure on 2008-09-29
How do I drag and drop with no Root access except via
 sudo -s or sudo passwd root
 other linux systems you login to root when required.

Thanks for your responses I was trying to get wifi working on a Dell 802.11g True Mobile 1370 using BCM43xx 14e4:4318 some forum help said download files then copy them into Ubuntu 8.04 file system ie.root then req.
I currently dual boot on this laptop with Vista Ultimate.

---

### Post by OldGrey on 2008-09-29
You could try "gksudo nautilus" in a terminal

---

### Post by MrWES on 2008-09-29
Not sure what you're asking here, but you might try making a desktop launcher with the following command:

gksudo nautilus

When you double click on it you will have a nautilus session running where you can drop and drag files.

Bill

Man....I'm gettin' slow!

---

### Post by hyper_ch on 2008-09-29
what do you need to drag'n'drop as root? Normally you don't have to do any such thing.

---

### Post by starcannon on 2008-09-29
Be careful moving files around as root. 

Maybe for now linking folders may be a tad bit safer? That can be done with a middle-click drag and drop, choose the option to create a link from the menu that pops up when you drop.

GL

---

### Post by rsambuca on 2008-09-29
> **hyper_ch said:**
> what do you need to drag'n'drop as root? Normally you don't have to do any such thing.

If you don't know the commands to use, or are a very slow typist, or just don't like using the command line, it can be much easier to use gksudo nautilus instead.

---

