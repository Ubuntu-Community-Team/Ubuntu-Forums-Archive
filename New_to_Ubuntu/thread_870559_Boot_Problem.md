---
title: "Boot Problem"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Ddub on 2008-07-25
First off I run a dual boot system constisting of an XP drive, an Ubuntu 8.04 drive and a storage drive. About a week ago I began loosing the storage drive (I/O errors and the like) so I bought another one. I also decided to reinstall XP (it had been forever since I first installed it). After doing that I swaped the hard drives around so I had my Ubuntu drive, my original storage drive, and my soon-to-be storage drive. Now when I boot using this configuration I get the error : 
   
   Try (hd0,0): extended or non-MS: skip
   Try (hd1,0): extended or non-MS: skip
   Error

This comes right after the bios does it's thing. And it only happens when I try to use the Ubuntu drive, the XP drive works fine except I can't remember how I configured wingrub so I can't dual boot either. Any help on these would be greatly appreciated

---

### Post by kdb424 on 2008-07-25
You need to reinstall. It will fix the boot loader.

---

### Post by Ddub on 2008-07-25
Will that solve both my problems? Also is there a way to reinstall with out formating?

---

### Post by mikazo on 2008-07-25
I Googled "reinstall grub" to see what comes up... maybe some of those sites can help. As far as I know, it is possible to resintall your bootloader without formatting.

[http://www.google.ca/search?hl=en&q=reinstall+GRUB&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=reinstall+GRUB&btnG=Google+Search&meta=")

---

### Post by alienexplorers on 2008-07-25
Try this it is super grub disk.  Fixed a lot of my problems.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by kansasnoob on 2008-07-26
If you actually have three separate hard drives you must also be sure that whichever drive "holds" GRUB is set to boot first in your BIOS.

---

### Post by Ddub on 2008-07-27
I tried super grub disk and it didn't work. At the start it was working fine (it went into it text menu right after boot) but when I told it to install Grub to Linux and MBR it tried to boot into Ubuntu and the screen went blank at the point gdm would normally start up. I'm tempted to just reinstall but would really rather not because I have dial-up and downloading all the updates, programs, etc to get back to point it was originally would be a massive pain. Fortunately most of the files that could be stored on the storage drive (the dying one)were and I recovered those.

---

