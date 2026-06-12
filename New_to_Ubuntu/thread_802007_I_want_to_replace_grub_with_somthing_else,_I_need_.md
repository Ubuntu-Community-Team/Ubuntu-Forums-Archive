---
title: "I want to replace grub with somthing else, I need a hand."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-05-21
*the short version of my problem*

I want to replace grub with lilo (or some other boot loader), and I am quite willing to edit files and such, but I have looked, and I can't find any guides that I feel that I can follow, can you please point me in the right direction.

*the long version of my problem*

I got a new laptop a few months back, and the cd drive worked perfectly in vista. it took less than a day, and I was completely sick of vista, so I installed ubuntu onto it from a 7.10 live cd. after a few days, I noticed that the cd drive didn't work, (refused to mount, and when you put a cd in, the light would flash, it would spin, and then nothing, no recognition by ubuntu) so, I decided that I would burn my cd in vista, booted into vista, and cd drive wasn't in device manager, nothing. it had been there a few days ago, but it was like vista had completely forgotten that I had a cd drive just after I installed ubuntu. it was pretty late by then, so I just went to bed, and forgot about the phantom cd drive. A few weeks later, I decided to ditch vista, in favor of xp, so I got an old xp disk, and installed it onto the vista partition (from an xp cd, I know that makes no sense, but read on). while I was there, I happened to notice that XP had recognized my cd drive. I thought this was pretty cool, so I downloaded a super grub disk, and replaced grub, so that I could use my cd drive in ubuntu, but I had the same problem as before. I booted back into xp, and the cd drive seemed to be missing again. 

finally, I stumbled across a comment on a blog, that asked if mandriva could be configured to use lilo, because grub was doing some crazy things with his nvida card, and stopping his cd drive from showing up. 
I laughed at that, and that he thought that the boot loader could mess up the cd drive, but then I thought, all the problems I had, where only occurring when I had grub. AND I could boot from a cd (which was before grub did anything) the only possible solution seemed to be, that grub was messing up my cd drive (I know this should be impossible, and if you can come up with a better explanation, I would love to hear it (no really), but untill then, I am going to go with grub is messing up my cd drive.

can you please help me install lilo, or some other boot loader, so I can get my cd drive working in ubuntu. Thanks in advanced.

---

### Post by Xiong Chiamiov on 2008-05-21
[A quick Google]("http://www.google.com/search?hl=en&q=lilo+ubuntu&btnG=Google+Search") gave me a [few]("http://ubuntuforums.org/showthread.php?t=96920") [posts]("http://ubuntuforums.org/showthread.php?t=370683") here, though they're rather old, since people mostly use GRUB nowadays.

---

### Post by iaculallad on 2008-05-21
I think you can't change your GRUB bootloader t LILO or such once installed after the installation. Choosing bootloader can only be done within the installation process. As such, use the Alternate CD so you have the option of choosing LILO instead.

---

### Post by iaculallad on 2008-05-21
I think you can't change your GRUB bootloader to LILO or such once installed after the installation. Choosing bootloader can only be done within the installation process. As such, use the Alternate CD so you have the option of choosing LILO instead. Or maybe, there's still a possibility.


**** -------- Sorry for posting this twice  ------------****

---

### Post by housam on 2008-05-21
if you got the chance to change to lilo, [[COLOR="Red"]_here_[/COLOR]]("http://www.control-escape.com/linux/lilo-cfg.html") is a link to how to configure it.

---

### Post by housam on 2008-05-21
[[COLOR="Red"]_Here _[/COLOR]]("http://www.icewalkers.com/download/lilo/943/dls/")is a link to download lilo

---

### Post by barbedsaber on 2008-05-21
I have lilo

(sudo apt-get lilo fixed that)

but how do I set it as my bootloader, I don't want to reinstall, but if I have to , I will.

---

### Post by housam on 2008-05-21
You have to create a lilo.conf file as shown in the link I gave you for reconfiguring lilo.
and I think you also have to remove grub after that and reboot.

---

### Post by kellemes on 2008-05-21
Exchanging Grub for LILO isn't going to change anything.. except for giving you a little learning curve in order to configure it.
I wonder.. is this drive recognized in BIOS?

---

### Post by barbedsaber on 2008-05-21
I got the alterrnative install cd, and fired i up in one of my old computer, I saw no choose bootloader thing, do you know where to choose, and if that works, I will reinstall on my main computer (the one with the phantom cd drive))

---

### Post by barbedsaber on 2008-05-21
> **kellemes said:**
> Exchanging Grub for LILO isn't going to change anything.. except for giving you a little learning curve in order to configure it.
I wonder.. is this drive recognized in BIOS?


yup, I would have assumed that it was a hardware problem, excet I can boot from it.

---

### Post by barbedsaber on 2008-05-21
I used the alternate install cd, (on an old computer) and I didn't see a choose bootloader thing, can someone please tell me where it is.

---

### Post by kellemes on 2008-05-21
> **barbedsaber said:**
> I used the alternate install cd, (on an old computer) and I didn't see a choose bootloader thing, can someone please tell me where it is.

[http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader")

---

### Post by barbedsaber on 2008-05-21
thanks, its late here, so I will look into it properly tommorow.

---

