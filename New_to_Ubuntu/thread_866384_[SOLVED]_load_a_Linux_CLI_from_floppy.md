---
title: "[SOLVED] load a Linux CLI from floppy"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rated727 on 2008-07-21
There are occasions when I would like to load _ONLY_ a Linux command line interface without all of the overhead of the X GUI and support for hardware that I don't need now.  Best case would be to load a "Bare Naked Linux" CLI from floppy.

There have been recent occasions when I have corrupted one of the initialization or configuration files for Xwindows with the result that X won't start, or starts without a working display 
... I can now logon to X and neatly shut it down with both eyes tied behind my back ... 

Things were even worse when I corrupted the GRUB config files which removes the option to start Ubuntu in 'recovery mode'

When that happens, I boot from the Ubuntu Live CD, open a terminal windows, then stare in frustration because I can't remember how to change the focus from the Live CD to the hard disk partition that holds the corrupted Ubuntu-Linux files.  At this point, Tweety Bird might say, "I t'out I taw a piec'o' cwap"

To describe this in Micro$oft-speak: Windows is corrupt and will not boot. I need to boot from a DOS floppy so that I can copy the registry backup files over the (now FOOBAR) registry.

---

### Post by Polygon on 2008-07-21
well, a live cd like you said would help, and if you cant figure out how to change to the hard drive which contains the borked os, you have to mount the hard drive first (either using the mount command or clicking on the icon on the desktop or 'computer'), and then you can 'cd /media/<drive name here> and it will get you to the hard drive

anyway, there are some floppy sized dos and linux things out there

linux ones:  [http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

and some dos ones: [http://www.bootdisk.com/](http://www.bootdisk.com/)

---

