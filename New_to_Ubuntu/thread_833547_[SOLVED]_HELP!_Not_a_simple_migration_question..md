---
title: "[SOLVED] HELP! Not a simple migration question."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by sydbat on 2008-06-18
I would like to apologize in advance if this has been discussed elsewhere in the forum, but my searches have been rather fruitless for my specific problem. If this has been discussed, please provide a link to the topic. If not, I hope this thread will be of assistance to others.

I am fairly new to the Ubuntu Experience. I like it – alot! Both of my boxes at home are running 8.04...one dedicated (32 bit) one dual-boot with XP Pro (64 bit). 

With the XP box, I was unable to install Ubuntu and be able to access it – I put it into it's own partition, it installed, but there was no grub or Windoz mbr for it. Thinking I did something wrong, I re-installed with the same outcome. So I decided to try the “Install via Windoz” option. Bada-bing. However, this still relies on XP not screwing up in some way for its stability.

My set up – 2 hard drives, each with 3 or 4 partitions containing various data (I learned a LONG time ago that multiple partitions keeps Windoz from corrupting things...and makes it easier to reformat every 6 months). One HDD is IDE and the other SATA. The SATA drive has both OS's – XP in the first partition and Ubuntu (as a windoz install) in the second.

My question is, can I 'migrate' from the windows installation to a 'full' installation, without going through a clean install of Ubuntu? If not, what do I have to back up so a clean install is easily re-customizable? As I am new to most of this, I appreciate detailed instructions...really...years of pointing/clicking in windoz has made my mind jelly...

Thank you in advance.

---

### Post by avtolle on 2008-06-18
Take a look at the Wubi Forum, and in particular the sticky about LVPM, which is to do the "migration" you desire.

---

### Post by sydbat on 2008-06-18
I saw that thread and it does not seem exactly what I need (or maybe it is and I am dumb).

I have no free partitions. The partition I want to put Ubuntu in already has Ubuntu (if that makes any sense) via the "windoz wubi install". Would LVPM allow me to overwrite the Ubuntu partition without losing any data (not that there is much data)?

Maybe my solution is a clean install because of how my drives are used. If so, I'll wait till I get a new SATA drive and put Ubuntu there.

---

### Post by avtolle on 2008-06-18
The Ubuntu installed by Wubi should be in the Windows partition, as it is treated as an application folder (for lack of a better term) by Windows; thus, it, itself, is not on a separate partition. I suspect that the Ubuntu that is on its separate partition is the one you installed earlier with which you had the grub, whatever problem. If I've misunderstood something, let me know.

---

### Post by avtolle on 2008-06-18
BTW, you should take a look through the forums concerning installation of Ubuntu on a SATA drive; there appear to be many problems that have been encountered, not insoluable, but problems nonetheless.

---

### Post by sydbat on 2008-06-19
Thanks. I'll check it out. If so, WOOO HOOO.

---

### Post by markbuntu on 2008-06-19
If you get a new SATA drive and put Ubuntu on it make sure it is in the first plug. SATA looks at each plug sequentially and boots from the first drive it sees with a boot sector. If you put your Ubuntu drive in the first plug, you can put grub there and not ever touch your windoze drive. Windoze will never even know about it.

---

### Post by sydbat on 2008-06-20
OK. Just checked in XP and my Ubuntu wubi install is in it's own partition. As I have no free partitions at this time, I guess I will do a fresh install...sigh. That is fine, as it will allow me to make sure nothing windoz related can screw it up.

I now need to know what to back up. My /home folder for sure...anything else? 

Also, my current config is 64-bit Hardy (8.04)...should I use the 32-bit version for overall better compatibility? Or stick with 64-bit?

Finally, the Ubuntu install is/will be on the SATA...should I unplug the IDE to make sure GRUB is placed on the right disk? (I ask this because of the problems trying to install before...which is why I chose wubi)

Thanks again for everyone's help.

---

### Post by markbuntu on 2008-06-20
If you are going to switch from 64bit to 32 bit you may have problems with a few of the ./config files in your /home directory but then again. you may not. Just be aware of that if some app starts acting up after you make the switch.

Set your bios to boot from SATA before PATA/IDE in the boot order and you should have no problems.

---

### Post by sydbat on 2008-06-20
Thanks mark, I'll check the bios settings.

I think I'll stick with 64-bit. My biggest problem was playing DVD's, but I figured it out - my LG DVDRW is borked...I'll just go buy another (fortunately they are cheap).

So, other than /home, any other file/directory to back up?

---

### Post by markbuntu on 2008-06-20
If you are going to do a clean install on a new hard drive, I see no reason to back up anything as long as you pay attention to which drive you are installing on and the installer will be pretty clear about that. But that is just my opinion. I am not big on safety.

I have amd64 on one hard drive and 386i on another. Hard drives are cheap these days.

My XP drive is in a box, on a shelf, in my closet.

---

### Post by sydbat on 2008-06-21
> **markbuntu said:**
> my Xp Drive Is In A Box, On A Shelf, In My Closet.
Yay!!!

---

