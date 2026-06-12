---
title: "[SOLVED] Wanting to install Ubuntu, again"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Cam_B on 2008-07-25
I am currently running openSUSE 11.0, and wanting to re-install Ubuntu because I am fed up with the fact that there are not a lot of apps that work with it, etc... and I miss the awesome support community.

But, this will be the 3rd time I have wiped my hard disk, and installed a new distro, not including the initial windows install. I have heard / read that re-installing an OS too many times can be detrimental to the HD. That makes sense, but just how many times will I have to wipe and re-install to start having noticeable effects, and what effects will those be?

tl;dr : I want to know the effects of wiping and re-installing an OS too many times on my HD, and how many times is to many.

Thank you in advance.

---

### Post by Thelasko on 2008-07-25
> I have heard / read that re-installing an OS too many times can be detrimental to the HD. 
I've never heard this.  Matter of fact, I had a friend back in the 90's who used to reinstall Windows 98 every 6 months because he claimed it would be too unstable otherwise.

---

### Post by alienexplorers on 2008-07-25
I wiped my hard drive about 5 times already.  Too much playing around with Ubuntu and messing it up with external programs.  This time I am sticking to what is in the repositories.

---

### Post by Thelasko on 2008-07-25
[Read this]("http://en.wikibooks.org/wiki/Minimizing_hard_disk_drive_failure_and_data_loss")

---

### Post by LowSky on 2008-07-25
I think your getting info a little  mixed up. Flash drives have a life span of read write cycles of only a few 100 thousands, while disc based drves will run a few billion, as long as the motor doesnt die. If my word means anything, I have install windows onto a certain drive more than 10 times with no issues, and ubuntu maybe more than 20, and nothing is wrong, it all performs the same as it did the first time. Don't get me wrong, drives do go bad but a few installs is nothing to worry about.

---

### Post by Cam_B on 2008-07-25
Ok awesome, thank you everybody for the help... I'm going to start backing up all the files I need and get Ubuntu back up and running.

---

### Post by candtalan on 2008-07-25
The hard disk is made to be able to work for incredibly long times repeatedly without problems. Installing something is not much different to normal daily use. Part of the disk is used as temporary area (virtual memory in windows and swap in linux) and is used a lot any way.

When in use the disk is spinning continuously (almost) and the read write arms are also in frequent use - normally anyway. The details are mind boggling and are not something to normally worry about for that reason.

Reinstall of windows I find to be inconvenient and tedious, but linux is much easier.  Although it is now not often required though for me.

To avoid reinstalling windows too, have you considered just removing the linux partitions and leaving the windows partition in place - then reinstalling ubuntu? A partition editor such as in the ubuntu Live CD parted or use of a smaller live CD such as parted magic is easy for this. Just delete all linux partitions and leave a space, don't make any replacement partitions (note 1). Then when you install ubuntu use the option to use 'the largest free space on the drive' and the install will leave windows untouched.

note 1:
in this case, the PC will not yet boot windows as it is, because the boot sector (mbr) expects a working linux partition. But this will be sorted out automatically during the ubuntu install. Or the windows command such as fixmbr can be used.

hth

---

