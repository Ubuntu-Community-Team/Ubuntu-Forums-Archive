---
title: "Installation disk doesn't do anything when I click install, memory test, etc."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Daniel_Garrison on 2008-05-28
I downloaded the Ubuntu .iso file for 8.04 (not the alternate text version).  I burned it to a CD and rebooted my desktop.  The disk fires up on boot and asks which language I would like.  I choose English and it brings me to the next screen.  From here I can choose to Install Ubuntu, perform a memory test, check the CD for errors, etc. (you all know the splash screen).  The problem is this; when I click enter on any of the options the CD drive light comes on and the drive starts to spin up but quits after nearly one full second, and nothing further happens.  I can click any of the option keys F4, F5, F6 for example and access the sub-menus but I'm not sure what these all do.

Any thoughts?

Thanks in advance,
Dan

PS.  I'm brand new to Linux, Unix, and of course Ubuntu, but I want to get away from Microsoft and the nightmare that it will become in the next decade.

---

### Post by radagast1155 on 2008-05-28
make sure you downloaded the right architecture. I would try to make another disk just to be safe also.

---

### Post by diablo75 on 2008-05-28
You might want to see if the firmware in the drive needs to be updated, or the BIOS version of the motherboard being older than the latest release from the hardware manufacturer (these things are easy to update if you still have Windows running on the system...otherwise, it gets tricky).  The alternate CD might also be worth giving a whirl if nothing else works.  I used to get ISOLINUX checksum errors all the time and couldn't install from a my DVD drive until the BIOS was updated to the latest version.

---

### Post by Oldsoldier2003 on 2008-05-28
> **Daniel_Garrison said:**
> I downloaded the Ubuntu .iso file for 8.04 (not the alternate text version).  I burned it to a CD and rebooted my desktop.  The disk fires up on boot and asks which language I would like.  I choose English and it brings me to the next screen.  From here I can choose to Install Ubuntu, perform a memory test, check the CD for errors, etc. (you all know the splash screen).  The problem is this; when I click enter on any of the options the CD drive light comes on and the drive starts to spin up but quits after nearly one full second, and nothing further happens.  I can click any of the option keys F4, F5, F6 for example and access the sub-menus but I'm not sure what these all do.

Any thoughts?

Thanks in advance,
Dan

PS.  I'm brand new to Linux, Unix, and of course Ubuntu, but I want to get away from Microsoft and the nightmare that it will become in the next decade.
some tips:
always burn the iso at the lowest speed possible on your burner with a good quality cd. you should also check the iso against its md5 sum to make sure you got a good download.

Unless you are planning to use the live cd to test your system, I've always had better luck using the alternate installer for actual installations. It's a text based "gui" so its not as scary as you might think based on the description :)

---

### Post by Daniel_Garrison on 2008-05-28
Ok so I'll check my firmware and update the bios.  If that doesn't work then burn a new disk at the slowest speed.  If that doesn't work I'll try the alternate disk (also burned at a slow speed to eliminate any extra steps).  That'll be my homework for tonight and I'll post again in the morning and let you all know if any of this solved the problem.

Thanks all,
Dan

---

### Post by diablo75 on 2008-05-28
I just wanted to add that the bug which was fixed by upgrading my BIOS had something to do with booting from a CD/DVD drive that's sitting on the same IDE channel as the primary hard drive (thats what the release docs said about that particular BIOS version and what it fixed).  I would assume that short of upgrading the BIOS, if I had moved some data cables around inside my PC and placed the DVD drive on the secondary IDE channel it would have also solved the problem...

---

### Post by Daniel_Garrison on 2008-05-29
So I tinkered around with this issue last night and did a bit more research on the web and came up with this (and I should have known):

Windows doesn't burn .iso image files (this is probably in the forums somewhere else but since I could read the disk I thought I had burned it correctly).

Apparently it (Vista) copied enough of the image correctly that it would allow me to select a language and show the splash screen.  The rest was useless.  So I did a google search for iso cd burning software and it came up with several free 3rd party programs that would copy an iso image file (can't remember which one but I'm sure they all do the same thing).  

In no time flat I had a Ubuntu 8.04 CD installation disk and was installing the new OS.

Thanks for your help guys.  I think I'm gonna like being a member around here.

BTW I love the new OS.  Being a total Linux n00b I was ready for a long struggle with installation.  Everything installed automatically.  Gotta love it. 

Later,
Dan

---

