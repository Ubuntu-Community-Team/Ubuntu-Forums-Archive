---
title: "[SOLVED] Noob problems with installing Ubuntu."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Tim_K on 2008-09-02
I'm working on installing Ubuntu 8.04 on a laptop to mess around with it and try some things.  It's a Dell Latitude CPi-A366XT.  366 Mhz P2 CPU. 

I'm using an older 4.5 GB hard drive and 256MB of RAM.

Upon running my Ubuntu CD (burned from the ISO), and with the hard drive freshly NTFS formatted, when I get to the screen that says "checking the installation / computing new partitions", I get a warning box that says "No root file system is defined, please correct this from the partitioning menu".

Now what do I do?  I tried searching here but didn't find an answer.

Once I get it working, I'll be installing an Orinoco Gold wireless PCMCIA card, Netstumbler 0.4.0 , and Airsnort for testing my wireless connection security.

Any help is appreciated!

---

### Post by Crafty Kisses on 2008-09-02
Delete the ext3 partition and leave a empty chunk of unpartitioned space on the drive. Use the Ubuntu installer to create at least two required partitions of / (root) and swap; you can make additional partitions on the same drive or a second drive for /home but that is optional. I'm guessing the installer is asking for swap partition assignment first and you are pointing to ext3 it will overwrite and still wants a root "/" partition at minimum assigned.

---

### Post by alienexplorers on 2008-09-02
Number one you don't use NTFS formatting on a ubuntu system.  Either use ext2 or 3 with 3 preferred.

---

### Post by jemate18 on 2008-09-02
> **Tim_K said:**
> I'm working on installing Ubuntu 8.04 on a laptop to mess around with it and try some things.  It's a Dell Latitude CPi-A366XT.  366 Mhz P2 CPU. 

I'm using an older 4.5 GB hard drive and 256MB of RAM.

Upon running my Ubuntu CD (burned from the ISO), and with the hard drive freshly NTFS formatted, when I get to the screen that says "checking the installation / computing new partitions", I get a warning box that says "No root file system is defined, please correct this from the partitioning menu".

Now what do I do?  I tried searching here but didn't find an answer.

Once I get it working, I'll be installing an Orinoco Gold wireless PCMCIA card, Netstumbler 0.4.0 , and Airsnort for testing my wireless connection security.

Any help is appreciated!


Try this step by step procedure with screenshots.....
Use the guided option "it will save you a lot of trouble"

> [http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

### Post by Tim_K on 2008-09-02
It seems to be working now, Thanks for the help!

How do I get the solved and thanks things to work?  I don't see anything to click on.

---

### Post by philinux on 2008-09-02
Thanks is the little medal bottom right and solved is a pull down from thread tools at the top.

---

