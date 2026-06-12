---
title: "LInux does not need to be rebooted like Windows?"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by CorneliusSneed on 2014-07-02
Ubuntu 14.04LTS. Don't worry, this is not one of *those *posts, I am mostly happy with Ubuntu. However, when I was thinking of switching from XP to Linux, one of the claims I saw frequently was that Linux doesn't need to be rebooted like Windows. However, now that I've made the switch, I am finding that in my experience at least, it does. Things start to act weird, and a reboot fixes it, just like when I was in Windows.

Ubuntu 14.04 LTS
Memory: 3.9 GiB
Processor AMD Athlon II X2 250 Processor x 2
Graphics  GeForce 9800 GT/PCIe/SSE2
OS Type 64-bit
Disk 192.5 GB

Not bleeding edge, but above the min sys req for most MMO's

I am not really complaining here, just wondering why so many people said I would not need to reboot?

---

### Post by bapoumba on 2014-07-02
Depends. When upgrading a kernel, you need a system reboot to run it. Most applications or programs wont need a reboot. You can restart the appropriate processes if you know them, or logout/log back in without rebooting.

---

### Post by fyfe54 on 2014-07-02
In my experience, rebooting is required for some things, but in general, it is waaayyyyy less than it ever was in Windows, and hardly ever because of weird behavior.

---

### Post by mastablasta on 2014-07-02
even kernel can be patched while computer is running. heh imagine Google doing constant reboots on their servers when something is wrong...

i have to use reboot to get the sound working. sometimes reboot makes it work, sometimes i need to turn it all off ocmpletely and uplug the power. that 's only on one maschine. the other one is working ok. usually they really do not need a reboot. raspbery pi with openelec had uptime of a few months. it's not much but would be more if my son didn't find the need to flip the switch on extension cord and by doing it cutting the power to the Pi.

also i was about to get the new record uptime on it when suddenly... PSU broke and i had to order a new one. :-(

---

### Post by grahammechanical on 2014-07-02
> [COLOR=#000000]Things start to act weird, and a reboot fixes it, just like when I was in Windows.[/COLOR]

I have not noticed that at all and for the last 3 years I have been a daily user of the development version of Ubuntu. Right now I am running Utopic Unicorn, which will become Ubuntu 14.10 at the end of October. There are updates to the code every day and I do not find that it starts to act a bit weird at all. And I expect weird things to happen on a development version.

A Linux distribution will give us endless opportunities to mess with the OS and it does not take much of a browse through the posts on this forum to notice that many people mess with the OS and then find it starts to act a bit weird. But I do not think that this is the same weirdness such as you report as happening in Windows.

People make all sorts of claims about Linux. Many do so out of a kind of hatred for Microsoft. I would not believe everything that people say about any computer operating system. 

Whether we are a single user or a business user running thousands of machines and servers it is the same Ubuntu for all of us. If Ubuntu had the same "weirdness creep" that Windows may have then use of Ubuntu would not be as widespread as it is.

[https://insights.ubuntu.com/2014/04/15/ubuntu-14-04-lts-the-cloud-platform-of-choice/](https://insights.ubuntu.com/2014/04/15/ubuntu-14-04-lts-the-cloud-platform-of-choice/)

For this thread to be a support question you need to define "weirdness." You may need to install some tools to monitor memory and CPU usage and in that way you may be able to identify a particular application that is not behaving neighbourly. Have you though of that? That this weirdness may be due to some application that you have installed and not down to Ubuntu at all?

Regards.

---

### Post by forbajato on 2014-07-02
I guess you would need to define weird in order to get much help.  There are a number of tools in the default Ubuntu install that will help you diagnose and rectify various types of weirdness but without more to go on it is hard to offer substantive help.

---

### Post by buzzingrobot on 2014-07-02
Kernels, video drivers, and other code that is loaded on boot will typically require a reboot when updated or added. The Update Manager should tell you when that's necessary.  (apt-get won't.)

If an application or other tool has a fault that sees it use memory and not release it when it no longer needs it -- a "memory leak" -- it will steadily consume more and more memory.  That, potentially, can impact performance by causing inadequate memory to be available otherwise. A reboot, or, often, just logging off and back in, will reset things.

---

### Post by oldfred on 2014-07-02
For example, my wife seems to have an issue with Thunderbird. If she runs the spell check it sometimes locks up Thunderbird. I can go to terminal, top to see which task it is and the kill that task. Thunderbird has always worked and sometimes still has original email with spelling error.

But do not just reboot, but remember the Elephants.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by philinux on 2014-07-02
> **CorneliusSneed said:**
> Ubuntu 14.04LTS. Don't worry, this is not one of *those *posts, I am mostly happy with Ubuntu. However, when I was thinking of switching from XP to Linux, one of the claims I saw frequently was that Linux doesn't need to be rebooted like Windows. However, now that I've made the switch, I am finding that in my experience at least, it does. Things start to act weird, and a reboot fixes it, just like when I was in Windows.

Ubuntu 14.04 LTS
Memory: 3.9 GiB
Processor AMD Athlon II X2 250 Processor x 2
Graphics  GeForce 9800 GT/PCIe/SSE2
OS Type 64-bit
Disk 192.5 GB

Not bleeding edge, but above the min sys req for most MMO's

I am not really complaining here, just wondering why so many people said I would not need to reboot?

Have you installed the nvidia driver from Additional Drivers in software and updates?

When it goes weird if you mean a slow down open a terminal with ctrl alt t and use the command top to see what's going on.

---

### Post by deadflowr on 2014-07-02
> **CorneliusSneed said:**
> 

I am not really complaining here, just wondering why so many people said I would not need to reboot?

I think you've misunderstood it.
This applies to updates, and not overall system integrity.

In Windows, generally speaking, when updates come they come in batches.
First you apply the first batch, and the system needs to be restarted for those updates to take effect.
Then after that restart, another batch of updates comes through that need to be updated.
Rinse and repeat.

In linux, all updates are applied in a single run.

All said, if something is causing you to need to reboot in both Windows and Linux(and not because of updates), then it may be safe to assume that something is not right with the machine.
But that's a guess.
Perhaps an example of what happens, in detail, could be helpful.
Like does the screen start blurring, or do apps suddenly freeze.

---

### Post by RedRat on 2014-07-02
I have found that there is a difference between a "Restart", such as recommended after updating the kernel, and a cold restart or reboot. I have a FreeAgent drive plugged into my USB port and when I do a simple "Restart", sometimes the system has trouble with FreeAgent (I store my music on it). Firefox sometimes also gets flaky after a restart especially if I was downloading pictures or other stuff in it to my FreeAgent drive. I found that if I turn the machine off completely and wait about 30sec and then reboot the machine from scratch. This usually solves this problem. These problems don't always happen so I suspect it has to do more with what was updated and how it attaches to the Linux kernel.

---

### Post by CorneliusSneed on 2014-07-03
Well, for example, I have trouble with my browser staying connected to the internet when watching videos, especially on YouTube. Usually it is a minor annoyance, only happening every so often, and either "refreshing" the connection or simply restarting the browser fixes it. However, sometimes it just hangs, or starts repeatedly disconnecting. When this happens, I restart the machine and it is fine, at least for quite some time.

Another thing is if I have something running that is graphics intensive, like Second Life. Most often everything is fine, but sometimes the machine just gets bogged down, and it takes forever to close anything I might have open. And again, once I reboot, no problem. This latter, however, I will admit could have more to do with the Second Life linux viewer than my OS. I don't know any other people running SL on linux that I can compare notes with.

---

### Post by Bashing-om on 2014-07-03
> **CorneliusSneed said:**
> Well, for example, I have trouble with my browser staying connected to the internet when watching videos, especially on YouTube. Usually it is a minor annoyance, only happening every so often, and either "refreshing" the connection or simply restarting the browser fixes it. However, sometimes it just hangs, or starts repeatedly disconnecting. When this happens, I restart the machine and it is fine, at least for quite some time.

Another thing is if I have something running that is graphics intensive, like Second Life. Most often everything is fine, but sometimes the machine just gets bogged down, and it takes forever to close anything I might have open. And again, once I reboot, no problem. This latter, however, I will admit could have more to do with the Second Life linux viewer than my OS. I don't know any other people running SL on linux that I can compare notes with.

Sounds like you could do with additional ram. Expanding to say 4 Gigs you would see a big difference.

[INDENT][INDENT]no such thing as too much memory
[/INDENT][/INDENT]

---

### Post by plucky on 2014-07-04
> **Bashing-om said:**
> Sounds like you could do with additional ram. Expanding to say 4 Gigs you would see a big difference.

[INDENT][INDENT]no such thing as too much memory
[/INDENT][/INDENT]

The OP has 4Gb of ram.

Could it be your swap partition is not working?

Please post output for ```
top
uname -a
```

---

### Post by CorneliusSneed on 2014-07-05
top:

top - 00:28:00 up 3:50,  2 users,  load average: 0.18, 0.16, 0.31
Tasks: 204 total,  1 running, 203 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.3 us, 3.3 sy,  0.0 ni, 88.3 id,  0.8 wa,  0.2 hi,  0.0 si,  0.0 st
KiB Mem:   4047980total,  2300220 used,  1747760 free,   102704 buffers
KiB Swap:  4192252total,        0 used,  4192252 free.  1148808 cached Mem 

uname -a:


ubuntu@ubuntu:~$uname -a
Linux ubuntu3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$

---

### Post by deadflowr on 2014-07-05
Well, I don't know much, as can clearly be noticed, but I did notice on Second Lide's wiki about linux viewer that there is a log file it generates.
It is in the secondlife folder, which is a hidden folder in you home folder.
Open the program "Files" and press ctrl + h, or click on menu item view > show hidden files/folders.

Hidden folders and files have dot at the beginning like .config.
Look for the folder marked .secondlife.
Then open it go to logs, and then SecondLife.log
Double clicking on it will open the text editor gedit.

If it isn't too big maybe post it, or at least some of it, if anything is even there.
If you wanted to post all of it, but it is actually really long, try pastebin
[https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

I don't know much about the youtube thingy, but with this it is at least a start.
One would think...

---

### Post by CorneliusSneed on 2014-07-08
Well, I have been waiting for an issue with Second Life, and so of course it has been doing the equivalent of looking innocent, twiddling its thumbs and whistling ever since I read your post. However, I did notice my HDD spinning up way more often than it should, and checked into that. I have since set my swappiness to 10, and it seems to have helped. Crossing my fingers in hopes that it continues to behave. ;)

---

