---
title: "Freshly installed Ubuntu is running very slow."
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Pagh on 2008-11-17
Hi I have a problem regarding Ubuntu 8.4 LTS.

Yesterday I installed windows xp and Ubuntu (dual boot). I have used Ubuntu for a long time as my only OS and it have always been running smoothly.
I started by installing windows on a 70 GB partition (sda2 - with NTFS filesystem) and then Ubuntu on a partition of around the same size (sda3. sda1 is a 25 GB backup partition with a ext2 file system). At first Ubuntu was running as good as ever but then after I installed all the software I wanted (through add/remove and CLI apt-get) and rebooted it suddenly became extremely slow!!!

When I look at the currently running/sleeping processes there is only the ordinary ones and no one is using any more CPU than normally.  

What is wrong, and what can I do to fix it??? 


Hope someone out there is able to help me solve this problem.

Regards Kasper Pagh

Ps. sorry for my bad english hope you have been able to comprehend me :-D

PPs. At the same time windows also stopped working (condn't boot) due to it missing a dll file called hal.dll.

---

### Post by Pagh on 2008-11-17
sorry to bump already guys but this is kinda urgent so... BUMP

---

### Post by Pagh on 2008-11-17
Hi I have a problem regarding Ubuntu 8.4 LTS.

Yesterday I installed windows xp and Ubuntu (dual boot). I have used Ubuntu for a long time as my only OS and it have always been running smoothly.
I started by installing windows on a 70 GB partition (sda2 - with NTFS filesystem) and then Ubuntu on a partition of around the same size (sda3. sda1 is a 25 GB backup partition with a ext2 file system). At first Ubuntu was running as good as ever but then after I installed all the software I wanted (through add/remove and CLI apt-get) and rebooted it suddenly became extremely slow!!!

When I look at the currently running/sleeping processes there is only the ordinary ones and no one is using any more CPU than normally.

What is wrong, and what can I do to fix it???


Hope someone out there is able to help me solve this problem.

Regards Kasper Pagh

Ps. sorry for my bad english hope you have been able to comprehend me

PPs. At the same time windows also stopped working (condn't boot) due to it missing a dll file called hal.dll.

---

### Post by darrenn on 2008-11-17
You can try to turn off visual effects. When my computer is giving me problems turning that off helps. Also closing firefox and restarting it helps speed up my system. Sometimes when I play videos they don't play at the proper speed this is only fixed by closing firefox and restarting. Sometimes I have twenty or thirty tabs open at once so this behavior is understandable.

Or you could uninstall all of that software and see if that fixes your problem.

---

### Post by LowSky on 2008-11-17
What exactly is running slow, could you post a copy of **top** from a terminal...
What kind of hardware are you running?
What programs are running at start up?
Are you using Compiz-Fusion?
Is indexing on?

---

### Post by oilchangeguy on 2008-11-17
since this is a new install for both operating systems. your best bet is to start over. and reinstall both operating systems. because it looks like you've been trying to change things in both linux and windows that have left you with an almost useless computer. after you reinstall both don't make any changes unless you're sure about what you're doing. ask questions first. microsoft has a forum for windows questions. [http://forums.microsoft.com/](http://forums.microsoft.com/) and this one:
[http://www.microsoft.com/windowsxp/expertzone/default.mspx](http://www.microsoft.com/windowsxp/expertzone/default.mspx)

---

### Post by Pagh on 2008-11-17
@darrenn I didn't even had the time to change to extra desktop effects before it stated;) But compiz is installed but not configured - so just standard effects there.

@lowSky I have already checked top and there is nothing unusual! Concerning the hardware it have always worked just fine. But sure I can list it:-D

AMD Athlon 64 Processor 3000+
512 Mb o' memory
ATI Radeon 9600 graphic card (I have always had kinda lot of troubles with that - can't recommend it to other users)
Some Realtek sound card - never had any troubles with it.
Don't thinks there is anything else of significance.
There is no additional programs running at startup. Only the ones that come pr default when installing the OS - as I said I didn't had the time to customize anything. 

I seriously can't figure out what is wrong!

Ps. I don't know what indexing is sorry!

---

### Post by overdrank on 2008-11-17
Threads merged :)

---

### Post by LowSky on 2008-11-17
> **Pagh said:**
> 

Ps. I don't know what indexing is sorry!

Goi to System> preferences> session

see if indexing is on at startup, turn it off. Also turn off other thing you may not use like, evolution calender, bluetooth. If you dont know if it can be turn off then just ask.

---

