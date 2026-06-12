---
title: "Noob question: 18.04.3 install on RAID 1 won't boot. Boot repair doesn't help."
date: 2020-01-10
forum: New to Ubuntu
---

### Post by jgvermeychuk on 2020-01-10
I am** new to ubuntu but have used UNIX in the past**. Performed a clean install of **ubuntu 18.04.3 on an HP machine with 2x1Tb drives in RAID 1 **config. Used the **BIOS setup to make a RAID partition before installing off the DVD**. The installation appeared to go OK, but** the machine did not boot**. Just a blinking cursor in the upper left of a blank screen. Downloaded and** ran boot-repair from the website.** Connected to the internet and **uploaded boot-info.** After boot-repair, the **machine still would not boot.** The **boot-info script is attached**, in two parts. [B]Any help would be much appreciated. Thanks in advance. 
[/B]

---

### Post by bunny9000 on 2020-01-11
Software / Motherboard raid or Raid card? I guess it's hardware raid since you were able to install the OS.

Did you make sure where you installed the boot loader in the right place and make sure you are using legacy or uefi depending on motherboard.

Check the boot order.

I don't know the boot repair tool you mention.

I've never installed ubuntu to my raid, but hardware raid the OS sees it as one drive and assignes it a single drive map so it shouldn't care that it's a RAID since the OS can't split the disk because it doesn't know there are two there.

But if you live boot via dvd or flash stick and ubuntu sees the one drive then at least you know the RAID is working and that ubuntu recognises it.

I'd sanity check all the 'things'.

You could also go darkside and install windows trial version. If that works with the raid you'd know it was something clunky either with ubuntu and your config or a miss step in the installation.

Sorry, I haven't read the boot script. 

I did just install ubuntu now and got a similar error. I rebooted 3 times and it only worked after I pressed F12 and it brough the menu up. Could just need the metaphorical hammer.

---

