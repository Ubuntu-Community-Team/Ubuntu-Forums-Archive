---
title: "Failed upgrade to 11.10"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by frogspawn on 2012-07-30
[SIZE=5][SIZE=4]I have a Wildebeest desktop and am attempting to Upgrade   to Natty Narwall 11.10 using the upgrade manager.[/SIZE][/SIZE]
 

 [SIZE=4]Because I have a very slow IP a friend provided me with a disk to preform this upgrade which I inserted. I subsequently found out that this disk was 11.10 and a 64 bit AMD version. This disk appears to be inappropriate for the current version and processor. [/SIZE] 
 

 [SIZE=4]During the download process, using the upgrade manager, the computer asks me to insert this disk. Clicking on continue allows me to continue the downloa , however, at the end it aborts after 1500 files and six hours indicating that three files failed to fetch. Two of these appear to be Amd 64.deb files and are requested, I suspect because the CD was inserted. [/SIZE] 
 

 [SIZE=4]I have tried this both ways, on several occasions both by inserting the disk and by bypassing it to no avail.[/SIZE]
 

 [SIZE=4]Can you please tell  me what I need to do to solve this problem.[/SIZE]
 

 [SIZE=4]Thanks in advance for your help.[/SIZE]
 [SIZE=4]Bill[/SIZE]

---

### Post by levlaz on 2012-07-30
> **frogspawn said:**
> [SIZE=5][SIZE=4]I have a Wildebeest desktop and am attempting to Upgrade   to Natty Narwall 11.10 using the upgrade manager.[/SIZE][/SIZE]
 

 [SIZE=4]Because I have a very slow IP a friend provided me with a disk to preform this upgrade which I inserted. I subsequently found out that this disk was 11.10 and a 64 bit AMD version. This disk appears to be inappropriate for the current version and processor. [/SIZE] 
 

 [SIZE=4]During the download process, using the upgrade manager, the computer asks me to insert this disk. Clicking on continue allows me to continue the downloa , however, at the end it aborts after 1500 files and six hours indicating that three files failed to fetch. Two of these appear to be Amd 64.deb files and are requested, I suspect because the CD was inserted. [/SIZE] 
 

 [SIZE=4]I have tried this both ways, on several occasions both by inserting the disk and by bypassing it to no avail.[/SIZE]
 

 [SIZE=4]Can you please tell  me what I need to do to solve this problem.[/SIZE]
 

 [SIZE=4]Thanks in advance for your help.[/SIZE]
 [SIZE=4]Bill[/SIZE]


A couple questions. 

1. What kind of specific hardware do you have? Processor, RAM, HD, etc. 

2. Do you have access to faster Internet? 

Best, 

Lev

---

### Post by TheFu on 2012-07-30
I'd assume this install/upgrade attempt is flushed and restore from a backup at this point.

A trip to a free wifi hotspot for an hour sounds like a really good idea to me at this point. I'd do a fresh install of either 12.04 or 10.04 from there. IME Ubuntu installs **really** want a live internet connection.  The normal 12.04 install takes forever (over an hour) to timeout if a network is alive, but can't reach the internet.  

Avoiding non-LTS versions is a good idea too if you don't have easy access for patching. That is just my opinion.

Loading x64 binaries on a x32-only processor shouldn't be possible, but if it did happen, it would be bad.  If you system was x32 and you intend to upgrade the OS, you should not use an x64 disk. To get to x64, you need a fresh install. [http://ubuntuforums.org/showthread.php?t=1213417](http://ubuntuforums.org/showthread.php?t=1213417)

---

### Post by codingman on 2012-07-30
1: 11.10 is Oneiric Ocelot, not Natty Narwhal.

2: what are your hardware specs? RAM, CPU, HDD...

3: I suggest you install 12.04, it is the latest version of Ubuntu available (that is stable). 

One other thing, try not to make your font so large, if you have trouble reading small text, use your own enlargening program, this way it does not make users do unnecessary scrolling.

---

