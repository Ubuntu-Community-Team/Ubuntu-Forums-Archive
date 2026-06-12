---
title: "need your help  please"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by kev1n40 on 2008-07-20
im very new to ubuntu and have tried to install the software but my xp system wont allow me to install new disc ive changed and reconfigured my bios as instructed but still no joy i can read the disc information but dont know what to do with it ive tried the install folder and that doesnt work maybe im doing loads wrong please can anybody help me get on with ubuntu so i to can enjoy what you seem to be enjoying thanks

---

### Post by ice60 on 2008-07-20
i think there's a windows installer called wubi, that way you can install it from windows i think.

just incase you don't know noramlly you don't need windows to install linux because linux is used instead of windows.

[http://wubi-installer.org/](http://wubi-installer.org/)
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

EDIT one thing i'd do before installing ubuntu is defrag windows first to help make room for ubuntu on the hard drive. if you really want to make sure you move all the files to the front of the drive to allow the most room possible you can run this defragger -
[http://www.dirms.com/](http://www.dirms.com/)
download DirMS-CL v2.2.1 and put it in the system32 folder, then open a dos prompt (start>run>cmd - then hit OK, and type in this -
**dirms c move lcn**
that just moves everything to the front of the drive, to defrag, then move the files to the front of the drive you run this -
**dirms c -q **
the page file won't be moved, so to move that you have to disable the page file, then re-enable it.

you might not need to do any of that, only if you need the space so don't worry about it lol

---

### Post by phidia on 2008-07-20
Is this an older computer you are trying to install to? Some computers cannot boot from the cdrom.
Or the cd could have been burned as data rather than a bootable iso? 
Check out the community documents on installation [here]("https://help.ubuntu.com/community/Installation").

---

### Post by kev1n40 on 2008-07-20
> **ice60 said:**
> i think there's a windows installer called wubi, that way you can install it from windows i think.

just incase you don't know noramlly you don't need windows to install linux because linux is used instead of windows.

[http://wubi-installer.org/](http://wubi-installer.org/)
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

EDIT one thing i'd do before installing ubuntu is defrag windows first to help make room for ubuntu on the hard drive. if you really want to make sure you move all the files to the front of the drive to allow the most room possible you can run this defragger -
[http://www.dirms.com/](http://www.dirms.com/)
download DirMS-CL v2.2.1 and put it in the system32 folder, then open a dos prompt (start>run>cmd - then hit OK, and type in this -
**dirms c move lcn**

thank you for that i shall try this a see what happens next

---

### Post by kev1n40 on 2008-07-20
> **phidia said:**
> Is this an older computer you are trying to install to? Some computers cannot boot from the cdrom.
Or the cd could have been burned as data rather than a bootable iso? 
Check out the community documents on installation [here]("https://help.ubuntu.com/community/Installation").

yes unfortunatly quite an older system will it still accept ubuntu?:confused:

---

### Post by ice60 on 2008-07-20
> **kev1n40 said:**
> thank you for that i shall try this a see what happens next

i re-editted my post about defragging, you probably won't need to bother, you can see how much free space you have with the default defragger windows comes with, it shows you after you click on analyze. 20GB is easily enough i think.

---

### Post by kev1n40 on 2008-07-20
> **ice60 said:**
> i think there's a windows installer called wubi, that way you can install it from windows i think.

just incase you don't know noramlly you don't need windows to install linux because linux is used instead of windows.

[http://wubi-installer.org/](http://wubi-installer.org/)
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

EDIT one thing i'd do before installing ubuntu is defrag windows first to help make room for ubuntu on the hard drive. if you really want to make sure you move all the files to the front of the drive to allow the most room possible you can run this defragger -
[http://www.dirms.com/](http://www.dirms.com/)
download DirMS-CL v2.2.1 and put it in the system32 folder, then open a dos prompt (start>run>cmd - then hit OK, and type in this -
**dirms c move lcn**
that just moves everything to the front of the drive, to defrag, then move the files to the front of the drive you run this -
**dirms c -q **
the page file won't be moved, so to move that you have to disable the page file, then re-enable it.

you might not need to do any of that, only if you need the space so don't worry about it lol

space as yet is not a huge problem just cannot get ubuntu to load from the cdrom i may be doing something so wrong  :lolflag:

---

### Post by ugm6hr on 2008-07-20
There are plenty of useful links in the Start here... thread linked below.

---

### Post by wpshooter on 2008-07-20
Kev:

1) are you trying to install Ubuntu from within M/S windows or are you trying to install it directly from a BOOTABLE Ubuntu ISO image ?

2) I would recommend that you do the latter and install it from a BOOTABLE Ubuntu ISO images - in which case you need to make sure of at least 2 things before you start, #1 being that you have BURNED the Ubuntu as an ISO image and not just meerly copied it as data, #2 make sure that your CD-Rom drive is the first boot device in your BIOS.

And since I think you said that this is a somewhat older machine, you probably want to download and burn the ALTERNATE (text based) version of Ubuntu as opposed to the Live (sometimes referred to as DESKTOP) version of Ubuntu.

P. S. - If your windows O/S or anything else on your computer is important to you, then I highly suggest that you have a backup before you start any of this.

Good luck.

---

### Post by kev1n40 on 2008-07-20
thanks i will try this

---

### Post by phidia on 2008-07-20
> **kev1n40 said:**
> yes unfortunatly quite an older system will it still accept ubuntu?:confused:

It depends on the specs-what are they?
See the system requirements within the link I inserted in my previous post. If the system is very old and/or has insufficent ram you might have to use a lighter distro (variation of linux).

---

### Post by kev1n40 on 2008-07-20
> **phidia said:**
> It depends on the specs-what are they?
See the system requirements within the link I inserted in my previous post. If the system is very old and/or has insufficent ram you might have to use a lighter distro (variation of linux).

127 gb
384 mb ram
300 mhz 
pentium 3 any good

---

### Post by ice60 on 2008-07-21
xubuntu might be better, it's just like ubuntu, but uses a slightly different desktop called xfce instead of the gnome desktop. xfce is lighter, but still really nice, i'm using it now.

if you want to try a really light and quick download you can try out austrumi (but you need to be able to boot from the cd drive to be able to use it, with a more powerful computer you can use vmware to run it from inside windows)

here's a picture of it -
[http://cyti.latgola.lv/ruuni/screenshoots/a-172a.jpg](http://cyti.latgola.lv/ruuni/screenshoots/a-172a.jpg)

here's the home page (click on the EN) -
[http://cyti.latgola.lv/ruuni/](http://cyti.latgola.lv/ruuni/)

it's only 85 MB so you should be able to download it in a few minutes. you download **austrumi-1.7.2.iso** from here -
[http://sourceforge.net/project/showfiles.php?group_id=103017&package_id=110546&release_id=606967](http://sourceforge.net/project/showfiles.php?group_id=103017&package_id=110546&release_id=606967)

then burn it to a blank disc using either of these programs -
[http://www.snapfiles.com/get/burncdcc.html](http://www.snapfiles.com/get/burncdcc.html)
[http://www.snapfiles.com/get/ISORecorder.html](http://www.snapfiles.com/get/ISORecorder.html)

then restart your computer with the new disc in the drive and, when asked, boot from the cd, as the computer starts up.

did you go in to the BIOS, right after the computer starts and before windows loads, to tell the computer to boot from the cd drive before the hard drive?

---

