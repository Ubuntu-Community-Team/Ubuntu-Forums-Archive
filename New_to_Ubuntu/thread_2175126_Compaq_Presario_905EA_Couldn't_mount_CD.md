---
title: "Compaq Presario 905EA: Couldn't mount CD"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by tobias5 on 2013-09-17
Hello,

I'm trying to install Lubuntu on an old laptop. Previosly I never had anything to do with Linux.

**What happened:**
- I burned the CD with the alternate ISO (file checked with md5 sum) of Lubuntu 13.04 ([https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO))
- Started laptop with the CD

- Installing process began (selecting language)
- I chose "Check disk for defects"

**The problem** (likewise happened if I directly chose "Install Lubuntu"):
"Detecting Hardware to find CD-ROM drives" progressed up to 97% then displayed the error message of
[I]"[!!] Configuring d-i
Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.
Retry mounting the CD-ROM?
<Yes>   <No>"[/I]

No matter what I tried (e.g. re-entering the cd), it didn't work.

Sometimes I got a second message:
[I]"Error reading Release file
The CD-ROM does not seem to contain a valid 'Release' file, or that file could not be read correctly. You may try to repeat CD-ROM detection but, even if it does succeed the second time, you may experience problems later in the installation. <continue>"[/I]

While executing another try to copy the messages into this post, there appeared a third message (which didn't appear all the 10-15 times I tried before):
[I]"[!!] Configuring d-i
Incorrect CD-ROM detected
The CD-ROM drive contains a CD which cannot be used for installation.
Please insert a suitable CD to continue with the installation."[/I]

Well, I thought the laptop has a problem with the CD-ROM driver. But the third message indicates a bad burn of the cd, doesn't it? If so, how can I make sure I'll burn a better one next time?

**Some hardware information:**
Compaq Presario 905EA
Mobile AMD Athlon(tm) XP 1800+ 1.52 GHz, 240 MB RAM
CD-Drive: TSSTcorp CDW/DVD SN-M242C


Well, I'd be glad about any help. Being used to pre-installed Win systems I never did anything like this. 

Thank you in advance!

---

### Post by sanderj on 2013-09-17
Possible causes:
- defect CD
- defect CD drive

First test: put the CD into another computer, boot it, and check the CD.

---

### Post by tobias5 on 2013-09-17
Putting the CD into another computer. Why haven't I thought of that? :D

I put the CD into the computer I used to burn the CD. The computer didn't find any error on the CD.


==> That means the problem lies with the CD drive, doesn't it? 
Might it help to burn the Boot-CD with the same computer and drive I want to use for the installation?

---

### Post by mörgæs on 2013-09-17
Hi, welcome to the fora.

The most likely problem is the 240 MB of memory. In order to verify that Buntu runs you can install the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") , but you will not get a useful system before you have found some more memory for that poor thing.

---

### Post by tobias5 on 2013-09-18
Are you sure there is no problem with the CD drive?

I could try to change the CD drive (I've got another one from a broken laptop). But if that is pointless I won't, of course.


I'm a bit surprised though, that 240 MB of RAM aren't enough. At least I understood the "System requirements" differently:
[I]"We have done many tests and we found out that Lubuntu  can be installed on a Pentium II or Celeron system with 128 MB of RAM,  but such a system would not perform well enough for daily use.  
[/I]
[I]With 256MB - 384MB of RAM, the performance will be better and the system will be more usable."
([/I][https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu))

So I do have to buy some additional memory? That's bad.

---

### Post by mörgæs on 2013-09-18
The Lubuntu gang is posting some very optimistic requirements. It gives people unrealistic expectations. 

Though it may be possible to *install* on 240 MB you will not be able to *run *a browser or a media player at a useful speed, but you should not worry about that now. First step is installing the mini.iso from CD (of course trying both drives) or USB and see how it goes. When we know the results from this you can decide next step.

---

### Post by tobias5 on 2013-09-18
Thank you for the advice.

I tried the mini.iso (downloaded from the page you posted) from CD. The installation process started and I got through the selection of language, keyboard, etc. Last I was asked to enter a name for the laptop in the network. Then there appeared some sort of command line. Unfortunately I don't have any idea what to enter there. Could you give me a link to some sort of tutorial or instructions?


In the beginning of the BOOT process I had to choose between "Install Ubuntu" and "Command Line Install" or something like that. Well I didn't know and therefore selcted "Help". Leaving "Help" the installation process started, so I don't know in which one I am.

EDIT: So far I wasn't asked how I'd like to partition the Hard Disk.

---

### Post by mörgæs on 2013-09-18
[http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

Please don't begin the 'post installation' part yet, just the first part of the install.

---

### Post by tobias5 on 2013-09-18
The installation worked this time. I think it didn't the first time, because I hadn't inserted the LAN wire in time.


The installation didn't follow the steps of the instruction exactly, but it worked. I didn't have to enter something into the command line.

There are some selections I didn't understand completely so I'll post them to let you check If I made a mistake. I chose:
[LIST]
[*]Installation of Linux Generic
[*]Targeted initrd
[*]Default value for Ubuntu (first one in list, because I didn't understand)
[*]Package"Lubuntu Desktop"
[/LIST]

Finishing the Installation the computer rebooted and I had to enter username and password. Then the system waited for my input. Because I didn't know what to enter there I simply turned the computer off by pressing the power button.

What's next? 

By the way: I encountered some old 256 MB RAM with PC2100 standard as requested from my computer. It was part of a bad working laptop so I'm not sure if it works properly. Should I put it into the computer? The "new" RAM was made by another company but seems to be of the same sort. My laptop said it (the laptop) had some 240 MB of RAM, a sticker on the RAM says 256 MB. I guess, both is correct in some way? So the old 256 MB and the new 256 MB from the bad laptop could work together?

---

### Post by mörgæs on 2013-09-18
Yes, give it all the memory sticks that it can digest regardless of brand.

After that try a new minimal install without choosing any packages in step 13.

---

### Post by tobias5 on 2013-09-19
I did a RAM check (feature of the Lubuntu Alternate Installer CD) with the "new" RAM and it detected lots of errors. So I'll just take out the "new" RAM. Well, seems like I have to buy some new RAM.

In the meantime I'll install Ubuntu another time without choosing any package in step 13. Could you explain the reason to me? I'd like to understand as much as possible. Thanks.

---

### Post by mörgæs on 2013-09-19
Used RAM is cheap on Ebay and other second-hand marketplaces.

You might have installed some too-heavy Ubuntu packages. Better to begin from a clean slate and see how it performs (when more RAM has arrived).

---

### Post by tobias5 on 2013-09-19
I expect my newly bought RAM to arrive on Saturday. Could you already describe the next step for me (when the RAM is in place and a new Ubuntu installation "clean")?

I won't have internet access the next two days and I am not sure if I can do anything on Sunday. So don't wonder if I don't post anything till Monday.

---

### Post by mörgæs on 2013-09-19
Just take your time. We are here when you get back.

When the memory has been added and the minimal ISO installation is done you only have to run the command

```
sudo apt-get install lubuntu-desktop
```

But don't expect the old Compaq to be fast. It will be usable, but not more than that.

---

### Post by tobias5 on 2013-09-28
Well, finally I'm back now.

I did the minimal ISO installation, got additional 256 MB of RAM (working) and installed Lubuntu with the command line you wrote. Thank you very much, I finally achieved to get Lubuntu working on my laptop! 

Only one small problem remains. After logging in I always get the Error message:

> Xfce Notify Daemon

Unable to start notification daemon

Another notification xndaemon is already running.

[->Quit]

What does this mean? As far as I can tell the system is working fine.

---

### Post by mörgæs on 2013-09-28
Good to hear. Welcome to the free world.

Which version number of Lubuntu did you install?

I don't know the daemon you mentioned. The only notification you need is a message when updated packages are available, and if that works you don't have to worry about more.

---

### Post by tobias5 on 2013-10-05
I'm sorry I don't know how to find out my version number of Lubuntu.

```
uname -a
``` results in > 3.8.0-31-generic #46-Ubuntu
```
lsb_release -a
``` results in > Ubuntu 13.04

I can't tell if any notification tool is working, because up to now none has ever appeared. Do you know some way to at least disable the error message?

---

### Post by mörgæs on 2013-10-05
Though the command says Ubuntu 13.04 you are in fact running Lubunut 13.04, which is great. The only downside is that you have to repeat the install in December for 13.10 when support for 13.04 runs out (but I guess you can do it quickly now).

I don't know more about the daemons nor the error message. Regardless of daemons, in order to keep the system updated you just have to run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

once in a while.

If you are good to go please mark the thread 'solved'.

---

### Post by tobias5 on 2013-10-05
Thank you very much for your help.

One last question: What does "repeat the installation" mean? Do I have to run the installation right from the beginning (overriding the whole harddrive) or just do some upgrade?

---

### Post by mörgæs on 2013-10-05
I think it's time for you to experiment on your own and learn from that. Asking questions is OK, but personal experience is better. In short: Try and see what happens!

My opinion about upgrades is stated in the link in my signature, but don't take it as the only truth.

---

