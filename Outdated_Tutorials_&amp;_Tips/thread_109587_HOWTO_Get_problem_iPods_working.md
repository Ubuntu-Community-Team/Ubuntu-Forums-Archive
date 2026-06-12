---
title: "HOWTO: Get problem iPods working"
date: 2005-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by sethmahoney on 2005-12-28
**The Scenario**
Here's what happened to me: I got a nice 4th gen iPod for Christmas.  I plugged it into my Ubuntu box expecting a couple bumps, but for it to eventually work.  It didn't.  I tried all sorts of mounting tricks, programs, and other sorts of nonsense.  I even recompiled my kernel THREE times (and for those of you who haven't tried, compiling the kernel takes a long time!).  Anyway, the third time, apparently, was the charm.

**The Bad News:**
1.  You have to recompile the kernel.  This is a bit scary, and it takes a while, but it is not at all difficult.  Fantastically written instructions can be found here: [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

2.  You have to disable USB 2.0 support.  This is fairly bad news, since USB 2.0 is quite a bit faster than 1.0 (which means that your song transfers will take a bit longer).  After playing around with gtkpod, though, this news isn't THAT bad - song transfers are still relatively fast.  Apparently there is an issue with the 2.6 kernel, USB 2.0, and the iPod that prevents them all working nicely together (some users have reported success with earlier kernel versions).

**The good news:**
Aside from recompiling the kernel, the process is really painless.  Here goes.

**Setting up your new kernel**
When you get to step four in the above-referenced kernel installation guide, make the following changes as well:

1.  From the main menu, go to "Device Drivers".
2.  From there, scroll down to "USB Support" (it is a ways down).
3.  **Dis**able "EHCI HCD (USB 2.0) support".
4.  **En**able "UHCI HCD (most Intel and VIA) support".

That's all!  Proceed with setting up your new kernel according to the instructions.

**Making it automount**
You only need to do this if an icon **doesn't** show up when you plug your ipod into your machine.  If it already does this, go ahead and skip this step.  Instructions for making your iPod automount can be found here (if you're using Breezy, you don't need to worry about the "killall gnome-panel" step):
[http://www.ubuntuforums.org/showthread.php?t=36632](http://www.ubuntuforums.org/showthread.php?t=36632)

**Using the software**
For some information on what software to use and how to use it, go here: [https://wiki.ubuntu.com//IPodHowto](https://wiki.ubuntu.com//IPodHowto)

Under Gnome I've had quite a bit of success with gtkpod v0.99.2 (this is not the version in Synaptic, but there is a deb for it floating around the forums) and iPodder for podcasts.  If you can't find the .deb, it should be fairly painless to install from source or to create a .deb using checkinstall.  I don't, unfortunately, have any info about KDE-specific software.

---

