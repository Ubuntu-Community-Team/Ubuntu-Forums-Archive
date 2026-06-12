---
title: "Live CD does not seem to be loading Grub"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Bryan P on 2008-08-18
Please help, I am new to ubuntu and am trying to create a dual boot system. I currently have a 250 Gb HD with XP only on it. I followed the Live CD install of 8.04 and all when fine. Ubuntu resized the hard drive half and half (xp and ubuntu)and ran the install completely then requested the reboot at finish. I rebooted and my pc booted right to XP, i never got a grub or any thing referring to Ubuntu. I used g-parted to check out the HD partitions and there were 3 partitions, 1 xp, 1 ubuntu and 1 swap.
So i rebooted agine and the same thing it goes right to xp and i can not boot into ubuntu. 

Any Ideas anybody

---

### Post by Elfy on 2008-08-18
Sounds like grub didn't get installed - you can do it from the livecd - this link should help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

follow the instructions, if you get errors post them.

---

### Post by Bryan P on 2008-08-18
> **forestpixie said:**
> Sounds like grub didn't get installed - you can do it from the livecd - this link should help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

follow the instructions, if you get errors post them.
Ok, Call me a real newbie. Now I have a real issue. Forget about the first issue altogether. The first install of Ubuntu is wiped out and so is the MBR. So now I can't even boot into XP. I tryed to reinstall Ubuntu and when it goes to resize the partition, it starts and then stops and says " resizing failed. The only good thing I got going right now is the fact that i can still see my XP partition even though i can't boot into it. 
I need to get rid of all traces of the old ubuntu partition and start from square one i think. But I am woried that if i mess around with this much more i'll mess up xp all together 

Siting and waiting, anyone

---

### Post by namegame on 2008-08-18
Your best option to prevent loss of data is to run the Windows XP repair utility which should be on the XP CD.

---

### Post by Bradtek on 2008-08-18
Boot from your Windows XP CD and follow this how to with screenshots
[Recovering Windows XP using the Recovery Console]("http://www.windowsnetworking.com/articles_tutorials/wxprcons.html")
Upto  the part where you get the Command Prompt
Then type either fixboot or fixmbr (or both)
You should then be able to boot into Windows XP

---

### Post by Bryan P on 2008-08-23
> **Bradtek said:**
> Boot from your Windows XP CD and follow this how to with screenshots
[Recovering Windows XP using the Recovery Console]("http://www.windowsnetworking.com/articles_tutorials/wxprcons.html")
Upto  the part where you get the Command Prompt
Then type either fixboot or fixmbr (or both)
You should then be able to boot into Windows XP
Thankyou, I forgot to write back, but your repair option worked. I have Ubuntu up and running now.

---

