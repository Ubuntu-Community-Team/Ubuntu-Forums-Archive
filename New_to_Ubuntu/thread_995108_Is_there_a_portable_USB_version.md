---
title: "Is there a portable USB version?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by humby on 2008-11-27
Hello,

I'm a total beginner in Linux.

So I decided (after some recommendations) to start with Ubuntu. Now, since this will be my very first attempt at it I prefer if I could install and run it from a USB drive - to minimize all installation and partitioning of my HDD (I currently run Win XP).

I read an article here:
[http://lifehacker.com/5070747/ubuntu-810-released-includes-bootable-usb-maker](http://lifehacker.com/5070747/ubuntu-810-released-includes-bootable-usb-maker)

and also this:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

But I didn't quite get how it all works.

Can someone direct me?

Thanks A LOT!

---

### Post by halitech on 2008-11-27
instead of trying to install it on a usb stick, why not try either the live cd (doesn't touch the hard drive at all) or install using WUBI (acts like an application to windows and can be removed from the Add/Remove Programs in windows)

---

### Post by tomtom1982 on 2008-11-27
Please try this:

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by humby on 2008-11-27
> **halitech said:**
> instead of trying to install it on a usb stick, why not try either the live cd (doesn't touch the hard drive at all) or install using WUBI (acts like an application to windows and can be removed from the Add/Remove Programs in windows)

Is this the Live CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Also - how would it save my settings if it doesn't write to the HDD, or am I missing something?

---

### Post by halitech on 2008-11-27
yes tht would be the link to the Live CD/normal install cd.

it doesn't save anything to the hard drive but if you just want to test it, it would be a good way without it touching your XP install. The Wubi is also good if you are nervous about messing up your XP install.

---

### Post by listener on 2008-11-27
The 'persistent' usb install such as the one linked to in a previous post, will allow you to save changes.  It will not be quite the same experience as with a hard drive install, however, and you'll need a large usb stick, like at least 4gb.  This is assuming you allow it to update after you install.  If you don't want it to update be sure not to allow it to do so.

best

---

### Post by humby on 2008-11-27
OK I decided to go with Wubi.

Some installation problems though:
[http://ubuntuforums.org/showthread.php?t=995216](http://ubuntuforums.org/showthread.php?t=995216)

---

### Post by jespdj on 2008-11-27
> **listener said:**
> ...and you'll need a large usb stick, like at least 4gb.
I have a persistent installation on an 1 GB USB stick - you don't need a 4 GB stick.

---

### Post by humby on 2008-11-28
> **tomtom1982 said:**
> Please try this:

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

Thanks for the article - it pointed me to another one:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

And I did everything as advised.

Now when I boot from my USB - I still get a bunch of options on how to proceed. I choose the one that says something like "Launch Ubuntu without making any changes to the HDD" is this what I should be seeing/selecting or I didn't do something right. I'm asking because when I boot from Live CD it seems to be giving the same options.

I realize the USB boot should be just like the Live CD, but I also wonder shouldn't be there some difference in the way it starts since it actually writes all settings back to the USB drive?

---

