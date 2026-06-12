---
title: "name that distro"
date: 2007-02-03
forum: Other OS Talk
---

### Post by fuscia on 2007-02-03
i have a 256mb usb memory drivey thing. just for the halibut, i would like to try to put a live distro on it. i'd like one in which my ipw2915 works out o'teh box, or wouldn't be too hard to get working. extra points for a high coolness factor and a tutorial targeting ****in' morons on how to put it on the stick.

---

### Post by glabouni on 2007-02-03
[Damn Small Linux]("http://www.damnsmalllinux.org/") ? [puppy linux]("http://www.puppyos.com/") ? 

[distrowatch's list of USB drive linux distro]("http://distrowatch.com/search.php?category=USB+drives&origin=All&basedon=All&desktop=All&architecture=i386&status=Active")

---

### Post by K.Mandla on 2007-02-03
SLAX. Start with the Popcorn edition and install it to that stick; you'll end up with ~128Mb of space for all the goodies you could want.

Installing modules is as easy as dropping them into a folder on the stick and they're automatically started and configured when you boot. I can't speak for the IPW2915, but there might be a [network module]("http://www.slax.org/modules.php?category=network") that would be of use to you.

I used to have a 128Mb stick that had the nvidia driver and Armagetron Advanced on there, so I could reboot at work and amuse myself during down times. It sparked infinite jealousy among co-workers.

Best of all, how's this for a tutorial? [http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/](http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/)

---

### Post by RAV TUX on 2007-02-03
> **fuscia said:**
> i have a 256mb usb memory drivey thing. just for the halibut, i would like to try to put a live distro on it. i'd like one in which my ipw2915 works out o'teh box, or wouldn't be too hard to get working. extra points for a high coolness factor and a tutorial targeting ****in' morons on how to put it on the stick.

[uL (Microlinux)]("http://www.ubuntuforums.org/showthread.php?t=352231")

should work fine and what would be cooler then running everything from command line?

if that doesn't hold the WOW factor for you stick with Puppy Linux

---

### Post by jdhore on 2007-02-03
2 words: Yggdrasil Linux

---

### Post by fuscia on 2007-02-03
> **K.Mandla said:**
> Best of all, how's this for a tutorial? [http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/](http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/)

so, i tried this and got as far number 4. when i right-click on *Makeboot.exe[i] and select [i]execute*, nothing happens. 

thanks for all the responses, you all. if i can get one of them working, i should be able to try out some of the rest.

[quote=rabid tux]what would be cooler then running everything from command line?[/quote]

home roasting and hand grinding my own coffee beans?

---

### Post by RAV TUX on 2007-02-03
> **fuscia said:**
> 


home roasting and hand grinding my own coffee beans?

:lolflag:...Now how did you know this is exactly what I do....and I only use a French Press!

I just thought of the perfect OS for your Pen Drive....dyne:bolic

---

### Post by igknighted on 2007-02-03
> **jdhore said:**
> 2 words: Yggdrasil Linux

If you're only gonna use two words, get you money's worth, right?

---

### Post by jdhore on 2007-02-04
> **igknighted said:**
> If you're only gonna use two words, get you money's worth, right?

i'm guessing no one knows about Yggdrasil....wow...an OS that hasn't released a new version in almost 12 years, the FIRST Linux-based OS to support Plug-and Play

---

### Post by K.Mandla on 2007-02-04
> **fuscia said:**
> so, i tried this and got as far number 4. when i right-click on *Makeboot.exe* and select *execute*, nothing happens. 
Ehrm, makeboot.exe is a [Windows executable]("http://www.bootdisk.com/bootdisk.htm") to make the USB bootable. :roll: You remember Windows, don't you fuscia? :D

Actually, I should've steered clear of tutorials that require Windows; I wouldn't use them either. I do remember that there's a good installer utility for SLAX that runs under Windows. I used it on my office machine when I made that USB I mentioned.

Would [syslinux]("http://packages.ubuntu.com/edgy/utils/syslinux") do the same thing? I'll try it and see. By the way, I'm only halfway enthused by the tutorials on pendrivelinux.com. It's rare that they work for me, and they seem somewhat ... esoteric, for lack of a better word.

---

### Post by fuscia on 2007-02-05
> **K.Mandla said:**
> Ehrm, makeboot.exe is a [Windows executable]("http://www.bootdisk.com/bootdisk.htm") to make the USB bootable. :roll: You remember Windows, don't you fuscia? :D

i guess so. :confused: 

> Would [syslinux]("http://packages.ubuntu.com/edgy/utils/syslinux") do the same thing? 

i have no idea. you lost me shortly after "plug in your computer and press the power button".

---

### Post by ahaslam on 2007-02-05
> **K.Mandla said:**
> Would [syslinux]("http://packages.ubuntu.com/edgy/utils/syslinux") do the same thing?

Yep, see here for a guide: [http://os.newsforge.com/os/05/07/08/1522251.shtml?tid=2](http://os.newsforge.com/os/05/07/08/1522251.shtml?tid=2)

It's also possible to install to usb from the live cd ;)

Tony.

---

### Post by Rumor on 2007-02-10
If you're still interested in this project, you might want to look at Flash Linux: [http://flashlinux.org.uk/](http://flashlinux.org.uk/)

Splash based boot system
Hardware autodetection
GDM based login manager
Gnome 2.8 desktop system with standard applets / utilities
Base packages - Evolution, Mozilla Firefox, Gaim, GEdit, VNC, TSClient, XChat

This leaves you with around 88Mb free on a 256 Mb key. This is 88Mb of compressable space, JFFS2 compresses everything on-the-fly, so you will get far more than 88Mb into the available space.
 Optional / extra packages:
   OpenOffice (Ximian release)
   Abiword , Gnumeric
   The GIMP
   Planner
   Firestarter (+iptables)
   VIM Editor
   Ethereal , Nessus
   Wireless kit for IPW2200
   Modem kit including HSF, SL and Speedtouch

---

