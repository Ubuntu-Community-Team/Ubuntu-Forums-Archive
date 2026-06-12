---
title: "MenuetOS, floppy os with a GUI"
date: 2005-11-10
forum: Other OS Talk
---

### Post by etc on 2005-11-10
[http://www.menuetos.net/](http://www.menuetos.net/)
I thought this was interesting, and you guys should have a look.  

It's written in ASM for 64bit and 32bit systems, and fits on a single floppy.  It doesn't touch the harddrive, and has a complete GUI.
It amazes me they could fit all of this on a single floppy.
The project developement is growing extremely fast.  The last time I checked this out, it didn't have half the stuff it does now.

They even have ports of things like ScummVM, Doom, Dosbox, and Quake. Check it out [http://www.menuetos.org/screens.html]("http://www.menuetos.org/screens.html")

Best of all it works in qemu!
Why not try it out, its a 1.4mb download

To use in Qemu 
Download 32bit img [http://optusnet.dl.sourceforge.net/sourceforge/menuet/m078.img]("http://optusnet.dl.sourceforge.net/sourceforge/menuet/m078.img")
Then
```
qemu -boot a -fda m078.img -pci -user-net
```
Replace m078.img with the name of the 64bit img if you use a 64bit system.
You can remove the -user-net flag if you don't want it having net access.

---

### Post by xequence on 2005-11-10
That looks very cool. I think I might have found a good OS for my old computer ;)

Edit:

Tried it in vmware, it messed up. On my accual computer it says hardware doesent support the graphics, and I have a normal old integrated intel graphics thingy.

Maybe two floppies for MenuetOS are in order, for better hardeware detection ;)

---

### Post by Kowalski_GT-R on 2007-11-01
i would be interested in this OS,

Has anyone had any experience with it?

Edit: please move this thread at will: I noted it's in the wrong place

---

### Post by ice60 on 2007-11-01
i've run it in qemu, here's a screenshot i took when i first ran it -

---

### Post by K.Mandla on 2007-11-01
Moved to Other OS Talk. ;)

---

### Post by n3tfury on 2007-11-01
> **ice60 said:**
> i've run it in qemu, here's a screenshot i took when i first ran it -

awesome!

---

### Post by MethodOne on 2007-11-01
Run this command on the image if you want a bootable CD:

```
mkisofs -b bootfloppy.img -o bootcd.iso bootfloppy.img
```[FONT=Verdana]Replace bootfloppy with the name of the floppy image and call bootcd whatever you want.  Then burn the resulting ISO onto a CD as an image.
[/FONT]

---

### Post by init1 on 2007-11-01
Menuet is great. Kolibrios is also worth mentioning. It's based on Menuet and has more applications.
[http://www.kolibrios.org/](http://www.kolibrios.org/)

---

