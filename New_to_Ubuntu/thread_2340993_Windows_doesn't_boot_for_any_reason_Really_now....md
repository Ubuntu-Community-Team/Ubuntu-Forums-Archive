---
title: "Windows doesn't boot for any reason? Really now..."
date: 2016-10-24
forum: New to Ubuntu
---

### Post by quiteunamusedvicki on 2016-10-24
Hello, I'm a new ubuntu user though I've used Mint previously. I installed Ubuntu because I wanted to try out what kind of thing it is. So far, I'm dissatisfied and I still prefer Mint but that's not why we're here right now.

First I'd like to say this laptop I have is at least seven years old. (Still runs like butter!:KS)
And also that I (obviously) have, or had, a dual-boot system. A fresh windows 7 and ubuntu on the side. One day I was normally using Ubuntu, then I switched to Windows to play a game, (Hustle Cat probably, since it's not Wine compatible) switched back to ubuntu  and I turned off my computer after I was done with it. I'm pretty sure I shut it down from the menu beside the clock, since I don't do it in any other way normally.

After that I left my computer for one day or two, I didn't need it. It was just neatly put into the corner. Then I turned it on and chose windows 7 loader from the GRUB menu, but it doesn't boot. Windows gets stuck on the playstation-like animation with four glowing balls. Then it shuts down and restarts to the GRUB menu. Ubuntu loads and works as normal. Windows doesn't. *sigh* Jealousy is bad for you.

I really don't know why would this happen. I didn't do anything major and I'm sure I didn't delete system32. I downloaded nothing. I changed no settings on neither of the systems. However I can still access the partition for Windows without any problem through ubuntu.

I'm known for breaking computers easily, but this is going too far. It's like *poof* no more windows. :(

I looked up for more threads on Ubuntu about this but they don't really match my case..? most included that windows broke after the drive was resized but I didn't do that, no need to.

I've probably done something really minor, stupid, and I'm just overlooking it. Sorry to bother.

---

### Post by rasmus91 on 2016-10-24
Hello to you.

Have you tried holding the Function 8 key  (F8) when windows starts booting, to activate Safe Mode? 

I would like to know if that works. :)

---

### Post by yancek on 2016-10-24
Your next step should be to get the boot repair software from the link below and download it on Ubuntu per the instructions on the site.  When you run it, select the option to Create BootInfo Summary and post a link to the output.  This will give us enough information to hopefully point out any problem.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mastablasta on 2016-10-24
so what is the ubuntu issue?

this has to do with something you did in windows 7. (safemode+restore last good point should solve it)

---

### Post by quiteunamusedvicki on 2016-10-24
> **rasmus91 said:**
> Hello to you.

Have you tried holding the Function 8 key  (F8) when windows starts booting, to activate Safe Mode? 

I would like to know if that works. :)

Hello to you too. Sorry for my really late reply.
I pressed F8 and tried "Safe mode" and "Safe mode with connection" both, and then it started loading some system files like normal, but then it "crashed." A moment of the blue screen and no safe mode on both options. I forgot to mention but this "a milisecond of blue screen" happens when I boot normally too. It's so fast I can't read it. I'm really curious why this is happening. Did I *really *happen to delete something important?

---

### Post by Geoffrey_Arndt on 2016-10-24
Vicki, before doing too much more (that could result in data loss on Windows partitiion) . . . . use your Ubuntu OS to save off all your key data to an external device.   Regarding Windows, . . . the boot report mentioned by masta above may help.   Many of us here at Ubu Forums haven't used Windows regularly in years (except perhaps to help Windows users get their data from malware infected Windows systems.).    You'd be the second person just today that I've read about with such issues, . . . anyway let us know what you can.   (note, by some chance, do you know if your system started a remote update to Win10???).

---

### Post by RobGoss on 2016-10-24
That blue screen if I can remember when I used Windows was called the blue **screen of death, **this is sometimes caused by a bad stick of Ram

In most machines there are usually two slots for the Ram how I determined which was bad was to remove one stick then boot the machine if it's boot as it should then that means the Ram you removed is probably bad and needs to be replaced you can repeat the process with removing the other stick and also rebooting the machine

You might also want to head over to the Windows forum and see if they have any fixes for this issue

As **Mastablasta** mentioned try a restore point it may solve the issue but if your Ram is bad it will need to be replaced

---

### Post by mastablasta on 2016-10-25
> **quiteunamusedvicki said:**
> Hello to you too. Sorry for my really late reply.
I pressed F8 and tried "Safe mode" and "Safe mode with connection" both, and then it started loading some system files like normal, but then it "crashed." A moment of the blue screen and no safe mode on both options. I forgot to mention but this "a milisecond of blue screen" happens when I boot normally too. It's so fast I can't read it. I'm really curious why this is happening. Did I *really *happen to delete something important?

what about command line boot?

you can boot form widnows install disk and use console to torubleshoot form there or use something like ultimate boot disk and do a fuil systems check to mkae sur ethere are no hardware errors (i.e. memtest for ram test and hard disk test, cpu and possibly GPU stress test).

> **RobGoss said:**
> That blue screen if I can remember when I used Windows was called the blue **screen of death, **this is sometimes caused by a bad stick of Ram


blue screen can be ram, but it can also be other things (missing files, corrupted system files, bad drive, bad sata cable, overheating ...). in any case it is usually a major error. by default blue screen is now disabled and the OS would rather issue a reboot if it can than show it. 


since you can't get into safe mode something is terribly wrong. but hard to say what from your posts (talking to OP here). i can only deduce the boot starts normally, so all is good there. GRUB (or the linux part) is not at fault then. this is either a hardware issue (can be troubleshooted with LIVE OS disk or specialised distro such as ultimate boot CD) or a Windows OS issue. 

the easiest solution (after you've made sure there are no hardware issues) is to simpley reinstall the windows (overwrite the current install) and update it. note that they have a service now that will do all windows updates at once so it is faster.  i think someone mentioned it here in the cafe section maybe. then all you need ot do is run a live linux OS and update grub or perform a "boot repair" to install grub and you should be good to go.
anyway that seems the simplest solution to me if oyu can't find the exact cause (just let the PC do it's work).

you may also want to do an antimalware scan from a live OS before attempting the reinstall (e.g. bitdefender rescue disc or avira rescue disk or similar...)

---

### Post by leunam12 on 2016-10-26
In Ubuntu, use "disks" utility to check disk health, since this could be related to bad sectors on the partition where your Windows reside and it gives you a IO error. I prefer to install and run "gsmartcontrol" but must users here are going to jump in and say that "disks" does the same thing, it's up to you. I used to buy a lot of used hard drives in the past but I don't do that anymore since most of them always had bad sectors and problems. Hard drives go bad really easy and many times without warning.

---

