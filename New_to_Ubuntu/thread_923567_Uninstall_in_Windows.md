---
title: "Uninstall in Windows"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Mimsy on 2008-09-18
I have a Compaq nc4010, without any optical drives at all. No floppy drive, no CD drive, nothing. I do not have access to the external CD drive.

I used Daemon Tools Lite to mount the Ubuntu 8.04 iso, with the intention to run from the live CD, but since the requires the system to reboot from CD, that does not quite work. It needs to boot Windows XP to run Daemon Tools to emulate the live CD.

I do see an option to Install Inside Windows, that is very tempting. Reading the description, it seems to allow me to install Ubuntu right from my desktop, and end up with a dual-boot setup.

Having done dumb things with computers in the past, I am resisting the temptation to immediately install, while I ask a few questions:

1. If it doesn't work, can the Ubuntu unstallation and partition be removed? How much of a pain is that?

2. How large should I make my Ubuntu installation? I want dual boot, so I can run WinXP for a fun little game I am severely addicted to, and then I want to run Ubuntu for everything else, and just mount the documents and music already on the laptop, in my Ubuntu installation. (Total HDD capacity is 60GB, currently 34GB of free space)

Thanks in advance!

---

### Post by Locutus_of_Borg on 2008-09-18
you can use the wubi installer to install while in windows, but i dont think using daemon tools like that will work

the latest ubuntu should have wubi included i think?

in any case some brief googling of "wubi ubuntu install" should give you a detailed guide

---

### Post by Paqman on 2008-09-18
Sounds like Wubi is prefect for you. Download and run the .exe from the [Wubi site](http://wubi-installer.org/). It'll grab the correct .iso disk image over the net and use it to install Ubuntu. No CDs required!

> **Mimsy said:**
> 
1. If it doesn't work, can the Ubuntu unstallation and partition be removed? How much of a pain is that?


Dead simple. Just boot into Windows and use the Add/Remove Programs manager.

> 
2. How large should I make my Ubuntu installation?

I'd give it 10GB if you aren't planning on using it to store data. You could probably get away with as little as 6GB, and it's not difficult to expand it later, but I always like to overestimate a little, since you never know what you'll be using the computer for in the future.

You Windows partition will be available at /host from within Wubi, so you can easily store all your data there and it'll be available to both OSes.

---

### Post by Mimsy on 2008-09-18
After looking at the Wubi web site, it does look like will be perfect. The screenshots in their FAQ also look exactly like the Install Inside Windows option from my 8.04 iso, and the FAQ states that Wubi comes on the 8.04 live CD, so I may end up using that one, since I am on a slow connection, and every little bit helps. :)

Thanks for the quick and helpful replies!

---

### Post by Paqman on 2008-09-18
From the Wubi site:
> 

Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.04.1 requires the Desktop 8.04.1 CD/ISO, while Wubi 8.04 requires the 8.04 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.04.1 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.


So you don't actually need to mess about with Daemon Tools, Wubi is clever enough to sort it out for you.

---

### Post by waspbr on 2008-09-18
alternatively you could make a live USB 

[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/]("http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/")

---

### Post by Mimsy on 2008-09-19
So far Wubi is working great, I'm posting from my new Ubuntu install now. Thanks again! :)

---

