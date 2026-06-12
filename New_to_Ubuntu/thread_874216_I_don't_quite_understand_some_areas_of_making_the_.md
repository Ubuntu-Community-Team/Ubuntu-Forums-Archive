---
title: "I don't quite understand some areas of making the computer dual boot..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Animeniac on 2008-07-29
I am about to install Ubuntu in my desktop PC and I want to make the pc dual boot with Windows Vista. I've read everything about dual booting windows and ubuntu in the official documentation and community documentation. I have already shrunk the c drive, using the Computer Managemnt, to 16 GB. I understand what to do, but I don't quite understand some areas of the installation. I have a few questions to ask you:

* How do I use the entire free space I've made without manually setting up the partitions, like using up the entire disk? If that is not possible, then what does the Ubuntu documentation mean by "twice the size of the system memory" for the swap partition?

* Is it okay that I don't install the GRUB boot loader? I told you I am using Windows Vista, and I'm sure can use the easyBCD program to make the computer dual boot Windows Vista and Ubuntu...

Thanks for your help.

---

### Post by tuxxy on 2008-07-29
Installing GRUB would be easier as it comes on the CD install, as for partitioning in the Ubuntu install, there is an option where you can select where the OS will be installed.

---

### Post by ConMan318 on 2008-07-29
I would just use the Windows partition editor to create an unallocated space big enough for Ubuntu.  Then pop in the liveCD and when it asks how to partition the disk, select 'use largest free continuous space'.

---

### Post by Animeniac on 2008-07-29
I already used the Windows partition editor to create the unallocated space of 16 GB.

---

### Post by Sef on 2008-07-29
> If that is not possible, then what does the Ubuntu documentation mean by "twice the size of the system memory" for the swap partition?

If you have 1 GB ram or more, then a 1 GB swap is the biggest you need to make.  The old rule ("twice the size of the system memory") was for computers with 512 ram or less.

---

### Post by steveneddy on 2008-07-29
Put that Ubuntu CD in, make sure all of your hardware works ok, like wireless, USB and sound.

If you're satisfied, pull the trigger and install that OS.

**[SIZE="3"]Yeah, man! GO, baby, GO![/SIZE]**

Sorry. Sometimes I let it get to me a little.

---

### Post by Animeniac on 2008-07-29
My compter has 512 MB RAM. How much space do I need to make the swap partition?

---

### Post by steveneddy on 2008-07-29
> **Animeniac said:**
> My compter has 512 MB RAM. How much space do I need to make the swap partition?

Twice the size of the RAM.

Get the calculator out:

512 + 512 = 1024

or

512 x 2 = 1024

Personally I like a little overkill, especially if you have a slower, older model of processor, so I'd make it as close to 1.5 gig as possible.

512 x 3 = 1536

---

### Post by jlenain on 2008-07-29
Hi all,

For 512mb of RAM, I would put 150% of the RAM in the swap, that gives 512+256=768mb in the swap. It is largely sufficient, since even with that, the swap won't get full before a long time of use. I did on a very old Dell laptop, with Ubuntu Hardy, and it is working perfectly.

As far as partitioning is concerned, an advice would be to use the partition editor providing on the Ubuntu live CD, at least for me it worked much better than Windows tool, and you can edit, resize, create, etc, partitions very easily with it if you choose the option 'manual partitioning'.

Cheers

---

### Post by bodhi.zazen on 2008-07-29
In general you should make your swap partition equal to your RAM X2, 1 Gb Max.

You can likely get away with a Swap of 512 Mb on most *modern* PC ...

However, if you have a laptop and wish to use suspend or hibernation then you need :

swap = RAM (or a wee bit larger).

---

### Post by steveneddy on 2008-07-29
But a slightly larger RAM won't hurt.

My laptop has 2 Gig RAM and I have a 3 Gig swap.

I know I really don't need that much swap, but there is always that just in case....case.

---

### Post by Animeniac on 2008-07-29
Is it okay if I don't install the GRUB boot loader? If I don't, what operating system will the computer run (Windows Vista or Ubuntu)?

The reason I am asking the questions about the GRUB boot loader is that I'm afraid that I will get a GRUB boot error. :eek:

---

### Post by bodhi.zazen on 2008-07-29
You should install GRUB and accept the default settings. The vast majority of the time GRUB works just fine and IMO 99 % of the problems with GRUB are due to FUD.

Since people are afraid of GRUB they change the defaults, and not knowing what they are doing, this results in errors.

GRUB is not fool proof, but grub errors are easily fixed or the windows boot loader re-installed.

Just curious, if you are not going to install GRUB, how then do you plan to boot Ubuntu ? Do you plan to configure the windows boot loader to boot Ubuntu then ? If you know how to do that, go for it, otherwise go with the defaults.

---

### Post by steveneddy on 2008-07-29
Listen to bodhi, he is old and wise.

---

### Post by ModdTaco on 2008-07-29
GRUB is great. Have yet to have a problem with it. More problems with windows messing up the MBR. Anyways NEVER use that infernal stock partioner in Vista. Your asking for trouble. Use the one suppplied with the Ubuntu disc or try and get a copy of Acronis Disk Director 10. It works wonders. You have to use it in Windows.

---

### Post by Animeniac on 2008-07-29
I don't know how to configure windows boot loader. I have the easyBCD installed in my computer.

---

### Post by MatthewPlanchard on 2008-07-29
I love this forum. ^_^ :) Woo!

Also, please do consider putting your root folder and your home folder on separate partitions. In the future when you get adventuresome and start to mess with settings, you will *most likely* make your system unusable at least once, and having a separate home partition makes reinstalling easy breezy lemon squeezy.

Haha!

Edit: For info on the aforementioned process, check out Psychocat's Resource Guide linked in my SIG. (nature).

---

### Post by Animeniac on 2008-07-29
> **MatthewPlanchard said:**
> I love this forum. ^_^ :) Woo!

Also, please do consider putting your root folder and your home folder on separate partitions. In the future when you get adventuresome and start to mess with settings, you will *most likely* make your system unusable at least once, and having a separate home partition makes reinstalling easy breezy lemon squeezy.

Haha!

Edit: For info on the aforementioned process, check out Psychocat's Resource Guide linked in my SIG. (nature).

That's exactly what I am going to do. I considered it before you even posted that message.

---

### Post by MatthewPlanchard on 2008-07-29
Preconsideration is the new consideration. Good show, mate.

---

### Post by Animeniac on 2008-07-30
I did it! I installed Ubuntu in my computer successfully! And I installed the GRUB boot loader, too, and it is working perfectly. Now I can dual boot Windows Vista and Ubuntu. Once again, thanks for your help, people. :)

---

### Post by bodhi.zazen on 2008-07-30
> **Animeniac said:**
> I did it! I installed Ubuntu in my computer successfully! And I installed the GRUB boot loader, too, and it is working perfectly. Now I can dual boot Windows Vista and Ubuntu. Once again, thanks for your help, people. :)

:guitar:

Welcome to Ubuntu ...

---

### Post by MatthewPlanchard on 2008-07-30
> **Animeniac said:**
> I did it! I installed Ubuntu in my computer successfully! And I installed the GRUB boot loader, too, and it is working perfectly. Now I can dual boot Windows Vista and Ubuntu. Once again, thanks for your help, people. :)

Congratulations, mano. Glad to see you've made it. Welcome, and enjoy the stay. :popcorn:

---

