---
title: "Ubuntu 14.04.5 Amd Driver support?"
date: 2016-11-14
forum: New to Ubuntu
---

### Post by tabletop2 on 2016-11-14
I am trying to find out if there is a way to install the actual driver for my graphics card Radeon hd 5770. i changed to ubuntu from linux mint due to issues with graphics, I eventually figured out that i would need to downgrade to 14.04 but the only option i found was 14.04.5 which apparently causes issues with my driver as well. when i try to change it from the Xorg driver it just refreshes back to the Xorg driver. I am really a Linux newb. Is there any one who can help me with this? I really like linux but i keep having to go back to windows due to tech issues that just leave me stranded in this big loop of forums that for some reason do not have my issue. Am i the only one with this problem?

---

### Post by gifford on 2016-11-14
If you need and earlier version of 14.04 instead of 14.04.5, you can find it here:[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
14.04.5 is using the Xenial kernel and X stack. The earlier release does not.

---

### Post by ajgreeny on 2016-11-14
I think you will need to use the 14.04.1 release point in order to get a kernel and xorg version that is both able to use fglrx and to have suppoort for the hardware stack.

DO NOT install 14.04.4 as the hardware enablement stack will lose support very soon, if it has not already done so so you would have to upgrade that to what you have now.  I am not even sure if the 14.04.4 point release will allow fglrx to be used so the safest way is to get 14.04.1 and reinstall; I do not know of any easy way to downgrade the enablement stack but it may be possible by removing the packages you have now with wily suffix to them, replacing them with the version that was in trusty at the start, and also installing the 3.13.0-## kernel series if they are now all gone, or were never on your system.

However, I have been looking for a site which still has the 14.04.1 version without any luck.  See if you can find it and have better luck than I have had.

---

### Post by mastablasta on 2016-11-15
> **ajgreeny said:**
> 
However, I have been looking for a site which still has the 14.04.1 version without any luck.  See if you can find it and have better luck than I have had.
need to go up the folder a bit and then you get this
[SIZE=2]http://releases.ubuntu.com/
[/SIZE]
at the bottom is this: "For old releases, see [old-releases.ubuntu.com]("http://old-releases.ubuntu.com/releases/"). "

the link then takes you to old images. Bookmark it and enjoy your 4.10 (Warty Warthog) download. :P



[SIZE=2]

[/SIZE]

---

### Post by ajgreeny on 2016-11-15
> **mastablasta said:**
> <snip>
Bookmark it and enjoy your 4.10 (Warty Warthog) download. :P
He-he!

I do just about remember trying that version, 4.10, before I moved fully to Ubuntu at 5.10, and stopped using WinXP.

[http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)
There you go!  get the version you need and update it but don't upgrade the hardware stack to anything else; stick with the 3.13.0-## kernel series and the provided series of xorg packages.

---

