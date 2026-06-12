---
title: "Removing Vista for Ubuntu"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by TrikeKid on 2008-06-25
So, I just won myself a pretty solid laptop on uBid, but it comes with Vista Home Premium on it. Will the ubuntu install completely eradicate this or do I have to do some work on my own? I have no interest in Vista. I'd rather just run Linux and learn as I go than try to work around any more windows BS. I just need to know that I won't have to partition around anything while installing my new OS.

---

### Post by sharks on 2008-06-25
this may help u:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by cdtech on 2008-06-25
Insert the CD and let'er rip. The install will format the disk for you.

Congratulations and good luck.

---

### Post by RomeReactor on 2008-06-25
Hi. When the installer asks you how to set up the partitions, select "**use entire disk**". This will completely remove vista, leaving the whole disk to Ubuntu.

However, try running Ubuntu in Live CD mode first to see if there are any issues detecting the hardware, so you now in advance what may come up once the system is installed..

---

### Post by WeEatVista on 2008-06-25
During the Ubuntu install, the on-screen options ask you how you want to partition your hard drive disk. There is an option that states: **Guided: Use entire disk.** That should completely replace all Vista with Ubuntu.

Hope this helps,

WeEatVista

---

### Post by TrikeKid on 2008-06-25
> **RomeReactor said:**
> Hi. When the installer asks you how to set up the partitions, select "**use entire disk**". This will completely remove vista, leaving the whole disk to Ubuntu.

However, try running Ubuntu in Live CD mode first to see if there are any issues detecting the hardware, so you now in advance what may come up once the system is installed..

I've already searched out all the hardware issues in the laptop forum, appears to me that the wireless and keyboard volume buttons are all that won't work without tinkering. It's an ACER Aspire 5570 if that makes any difference. I just wasn't sure because I've never had a computer with a restore partition, the newest computer I've had is this desktop built in '02.

---

### Post by RomeReactor on 2008-06-25
> **TrikeKid said:**
> I've already searched out all the hardware issues in the laptop forum, appears to me that the wireless and keyboard volume buttons are all that won't work without tinkering. It's an ACER Aspire 5570 if that makes any difference. I just wasn't sure because I've never had a computer with a restore partition, the newest computer I've had is this desktop built in '02.

In that case, as WeEatVista says, use the 'Guided: use entire disk' option; the install should be pretty straightforward and it will remove vista completely.

---

### Post by dinomite89 on 2008-06-26
Have you considered Dual Booting, (depending on how big the HDD is in your laptop), the only reason i say i because the first time i tried to install Ubuntu about a year ago i got over ambitious and wiped windows, got fed up with trying to get Linux to work and had to start form scratch again, now i dual boot between Hardy Heron and Vista x64, just a a thought.

---

### Post by bobpur on 2008-06-26
Before you wipe Vista off that machine, you might want to make the restore disk set just in case you ever want to sell it in the future. The less enlightened consumer might not appreciate a linux machine. :) :)

Just a thought-- If you can find all the XP drivers for that machine and then duallboot with Ubuntu & XP You would be happier with that laptop. Then you could take that Vista disk set I mentioned earlier down to the local skeet range and really have fun with it. Or not.

---

### Post by kansasnoob on 2008-06-26
> **dinomite89 said:**
> Have you considered Dual Booting, (depending on how big the HDD is in your laptop), the only reason i say i because the first time i tried to install Ubuntu about a year ago i got over ambitious and wiped windows, got fed up with trying to get Linux to work and had to start form scratch again, now i dual boot between Hardy Heron and Vista x64, just a a thought.

I much prefer a dual boot also! Whether it's with a working win os, or a working linux os,I know if the new os just doesn't work I can easily revert just by tweaking the mbr/grub and keep on partying!

---

### Post by Canis familiaris on 2008-06-26
I suggest:
Partition Manually:

Assuming you have a 40GB hard disk. If you have larger or smaller disk, change the size in same ratio.
In the live CD
Go to System->Admininstration

First delete all your existing partitions.

(1) Create a partition of about 12GB, format it as ReiserFS and set the mount point as / during install.
(2) Create another partition of about 20GB, format it as ext3 and set the mount point as /home during install.
(3) Create another partition of either size twice your RAM or 256MB more than your RAM (whichever is less) and format it as SWAP.
(4) Reserve the rest of space by creating an extended partition.

Now install Ubuntu.

---

### Post by TrikeKid on 2008-06-26
Is there a way for me to burn the restore partition onto a cd? I've never dealt with one of these deals before, all my computers have come with restore disks.

Anurag, It's got a 160 gig disk.

I'd rather jump in both feet to ubuntu than try to deal with Vista. I've used Vista on borrowed machines and it wasn't for me.

---

### Post by thomsany on 2008-06-26
Vista is the worst mistake Microsoft could have made.
Sacrificing security and performance for looks is not the best way to go!
I have been going back and forth between windows and ubuntu until I finally made my switch to Ubuntu completely.
Haven't looked back at all... good luck!

---

### Post by dinomite89 on 2008-06-26
TrikeKid,

How about reformatting, and setting up dual boot with XP, i know you want to do away with windows but Linux can be real difficult, trust me i learned the hard way.....just don't want to see someone make the same mistakes that i did.

Out.

---

### Post by stalkier on 2008-06-26
To be honest I have heard some people having issues installing other OS over Vista.I have had no such trouble though. Not sure why they have trouble...perhaps they are not PC savvy??? Who knows. Anyways good luck to you. I hope you enjoy it.

---

### Post by TrikeKid on 2008-06-27
> **dinomite89 said:**
> TrikeKid,

How about reformatting, and setting up dual boot with XP, i know you want to do away with windows but Linux can be real difficult, trust me i learned the hard way.....just don't want to see someone make the same mistakes that i did.

Out.

The problem there would lie in me obtaining XP to dual boot with. 
I don't have a problem with XP, once it's been whipped and filleted into the proper shape, it's not bad. My GF runs a cleaned up version of XP on her computer with less thatn 1ghz processor and I think 256MB of ram and it runs faster than the computer I'm using now (which I share with my parents) that has a 2.4ghs P4 and 512DDR ram running XP home.

---

### Post by FranMichaels on 2008-06-27
Just see how Ubuntu behaves with the livecd, if everything works, then why not? 

I did dual boot Ubuntu with XP, in 2004, and I never used it as much because of the hassle of rebooting (I mean if you're in the middle of doing something or what have you, that other OS isn't going to get booted into...)  

Once I had put Ubuntu on my laptop as the sole OS (2005.) Well, I just fell in love with the Linux way (and okay the dead easy Ubuntu way too.)

Go for it! :guitar:

---

### Post by Canis familiaris on 2008-06-27
Wrong Post!

---

### Post by Canis familiaris on 2008-06-27
I would suggest to go the partitioning way I suggested above (only multiply the partition size by 4) and install Ubuntu Hardy. Leave some space in the extended partition so that you can install XP anytime if needed. Also keep Super GRUB disk in handy which help to recover your GRUB it is overwritten.
Even more so I suggest that if you really need XP then you can run it in VIrtualbox.

[See this screenshot]("http://amitech.50webs.com/ultimate.html")

---

### Post by crackerjack1948 on 2008-06-27
I'am new to this but i set my xp on a small hdd at cable select, then installed my ubuntu on my 200 g hdd, It boots ubuntu first. I really like this system. I use xp only when i must!!!!!!

---

### Post by nothingspecial on 2008-06-27
If you totally nuke Windows you`ll soon become proficient with linux.

---

### Post by muteXe on 2008-06-27
I would dual-boot to be honest, until you are 100% sure and happy that you want to stick with linux.

---

### Post by john29485 on 2008-07-22
Hi I saw this post regarding uBid and thought I would pass along a site that help bidding on uBid by sniping.  The site is [www.bidnapper.com](www.bidnapper.com) and I believe support for uBid is free.
John

---

