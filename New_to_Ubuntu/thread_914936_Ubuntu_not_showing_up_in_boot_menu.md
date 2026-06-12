---
title: "Ubuntu not showing up in boot menu"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by tallpaul66 on 2008-09-09
I installed Ubuntu and gave it an entire hard drive to use. When it finished installing and the computer rebooted there was no dual boot option. It booted straight into XP. Is there a way to manually edit boot.ini so that I can run Ubuntu? I do not remember seeing an option for dual booting during the install process.

---

### Post by BDNiner on 2008-09-09
I would recommend using grub as your bootloader, i don't believe boot.ini will allow an option for ubuntu to be added to the boot menu. there are posts for installing ubuntu dual boot system with two harddisks in these forums. i just can't find a link for the life of me right now.

---

### Post by Bucky Ball on 2008-09-09
Try supergrubdisk. 

[www.supergrubdisk.org](www.supergrubdisk.org)

Download iso, burn a cd and boot from it. That should set up your grub for you. You can do this manually, but to get up and running quickly, this could be the shot.

---

### Post by tallpaul66 on 2008-09-09
I found lots of threads on how to get windows back onto the boot menu but none on adding ubuntu to the bootg menu. Maybe I didnt look hard enough.

---

### Post by bumanie on 2008-09-09
This problem indicates that grub did not install itself to the MBR or your bios is not set to 'look' for a second hard drive. Check your bios settings and if that is OK, post the output of terminal code > sudo fdisk -lu You will have to do this from the live cd as you cannot boot into ubuntu.

---

### Post by BDNiner on 2008-09-09
the reason you booted straight to XP is because windows is using its bootloader. you will need to install grub or other linux bootloader inorder to have the option to choose ubuntu. Check you this post for restoring grub:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by mikewhatever on 2008-09-09
> **tallpaul66 said:**
> I installed Ubuntu and gave it an entire hard drive to use. When it finished installing and the computer rebooted there was no dual boot option. It booted straight into XP. Is there a way to manually edit boot.ini so that I can run Ubuntu? I do not remember seeing an option for dual booting during the install process.

You must have more then one HDD. In the BIOS, switch their boot oder so that the one with Ubuntu is the first to boot from.

---

### Post by cdtech on 2008-09-09
There is a method to edit the boot.ini file in windows to boot Ubuntu using the Windows MBR but it's a bit confusing. You just need to reinstall the GRUB bootloader using the Live CD.

---

### Post by presence1960 on 2008-09-09
Hi everyone, I am new to Linux. I had kind of the same problem except I added Vista after Ubuntu. Each has their own hard drive. When I booted the Vista dvd i kept getting the message there are no partitions Windows can be installed to. I thought this out for a minute, went into BIOS and switched my first boot drive to the one I was going to install Vista to. Was then able to install Vista. Went back into BIOS and put my Ubuntu drive as first boot and upon booting Grub had the option for Windows. I didnt have to edit a thing. I gotta say I have been using Ubuntu for about a month and a half and I really appreciate the fact that I have not had to tinker with or troubleshoot anything. The confidence is there that when I run Linux I will spend my time doing what I need to do instead of tinkering around with the OS. Unfortunately I need to keep Windows for work (bummer).

These forums have really helped ease me into the transition to Linux, espescially the command line. But with everyone's help I can say I have had no problems so far. As I am back to being a beginner again these forums have really made the difference for me.

---

### Post by cdtech on 2008-09-09
> **presence1960 said:**
> 
These forums have really helped ease me into the transition to Linux, espescially the command line. But with everyone's help I can say I have had no problems so far. As I am back to being a beginner again these forums have really made the difference for me.
I'm just outside of Pittsburgh.
Go Steelers......:)

---

### Post by presence1960 on 2008-09-09
I am in Philadelphia, 1/2 mile from the stadiums complex. BUT I am not an Eagles fan. The raiders have been my team since 1966, even tho they stink now I aint changing teams...Go Raiders

---

### Post by Bucky Ball on 2008-09-10
[quote=tallpaul66]:
                                                                      *Maybe I didnt look hard enough.*[/quote]
                                 
Didn't have to look far. My post from above that one.

     [QUOTE=Bucky Ball][I]Try supergrubdisk. 

[www.supergrubdisk.org]("http://www.supergrubdisk.org/")

Download iso, burn a cd and boot from it. That should set up your grub for you. You can do this manually, but to get up and running quickly, this could be the shot.[/I][/QUOTE]

:)

---

### Post by Bucky Ball on 2008-09-10
> I had kind of the same problem except I added Vista after Ubuntu.

This can be very problematic as Windoze demands the first partition. Normal routine is to install windoze first, then Ubuntu. It must also be installed on a primary partition, not logical. Ubuntu doesn't mind either. :)

---

### Post by caljohnsmith on 2008-09-10
> **Bucky Ball said:**
> This can be very problematic as Windoze demands the first partition. Normal routine is to install windoze first, then Ubuntu. It must also be installed on a primary partition, not logical. Ubuntu doesn't mind either. :)
Actually, you don't have to install Windows to the first primary partition, and you can even install it to logical partition and get it working without too much hassle. But one of the problems with installing to a logical partition is that you may not be able to do a "Windows Repair" from the Windows Install CD if the need ever arises. So bottom line, I agree with you, Bucky Ball, that one should use a primary partition when possible. :)

---

### Post by Bucky Ball on 2008-09-10
Thanks for that, caljohnsmith. Interesting. Just been reading this page after reading your post ... learn something everyday round here ...

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

\\:D/

---

### Post by caljohnsmith on 2008-09-10
> **Bucky Ball said:**
> Thanks for that, caljohnsmith. Interesting. Just been reading this page after reading your post ... learn something everyday round here ...

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

\\:D/
In that article you linked to, they fixed their boot.ini file by running the "bootcfg" command; from what I've heard that command does not always reliably fix boot.ini. I think the best guide I've seen for booting Windows from a logical partition (without just putting its boot files on a primary partition), is the guide that forum member meierfra put together:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

He even figured out how to boot Windows Vista from a logical partition. :)

---

### Post by presence1960 on 2008-09-11
Windows is installed on a primary partition, it is a Seagate 160Gb IDE drive, Linux is installed on a Seagate SATA 250 GB drive. The problem was when I went to add Vista (unfortunately I need it for when I bring work home) the DVD would tell me  that Windows could not find a partition to install Windows to. I went to Bios and made the IDE drive first boot and then was able to install Windows. When installed went back to bios and made the SATA drive first boot. At that point once I restarted the machine grub already had the Windows option there. I just tested what was said about the repair function and as long as I go to BIOS and switch the Windows drive to first boot the repair disk works. I want to learn more about Linux so I tested what you said and the repair function works fine.

---

### Post by caljohnsmith on 2008-09-11
> **presence1960 said:**
> Windows is installed on a primary partition, it is a Seagate 160Gb IDE drive, Linux is installed on a Seagate SATA 250 GB drive. The problem was when I went to add Vista (unfortunately I need it for when I bring work home) the DVD would tell me  that Windows could not find a partition to install Windows to. I went to Bios and made the IDE drive first boot and then was able to install Windows. When installed went back to bios and made the SATA drive first boot. At that point once I restarted the machine grub already had the Windows option there. I just tested what was said about the repair function and as long as I go to BIOS and switch the Windows drive to first boot the repair disk works. I want to learn more about Linux so I tested what you said and the repair function works fine.
It sounds like you installed Vista to a primary partition though. Is that true? What I mentioned to Bucky Ball is the special case when you install Windows XP/Vista to a logical partition, and then you later try to use the "repair" function from the Windows Install CD. If you did install Vista to a logical partition though, please let me know. :)

---

### Post by presence1960 on 2008-09-11
Vista is on a primary partition. I appreciate what everyone shares on here. I am a newbie to linux and want to learn, not only to be good at this but because I hate Windows enough to be motivated...LOL. There seems to be a different atmosphere here. I have been browsing the posts and I haven't come across any flame wars yet. I am sure there are disagreements or differences of opinion but the whole outlook here is conducive to sharing experiences and knowledge for all to benefit.

---

### Post by Bucky Ball on 2008-09-11
From this page:

[http://www.ubuntu.com/products/WhatIsUbuntu](http://www.ubuntu.com/products/WhatIsUbuntu)

> **[B]What does Ubuntu mean?** [/B]

 [LEFT] Ubuntu is an African word meaning 'Humanity to others', or 'I am what I am because of who we all are'. The Ubuntu distribution brings the spirit of Ubuntu to the software world. [/LEFT]
Welcome, Enjoy and don't forget to ask questions when this happens: ](*,)

Also, if your problem is fixed you can go to 'Thread Tools' and mark it 'solved' so others can surf here for a solution or clue to their problem. :)

---

### Post by vwxy155 on 2008-09-11
Hopefully the proc rate on these beauties is enough to justify taking them over a cloak enchantment, but I imagine that if it's not, Blizzard will bump it up. Our services are here to help new or casual players level up quickly and efficiently. Our [powerleveling](http://www.wowgold800.com/) services will get your character to your desired level, with [wow gold](http://www.wowgold1000.com/) and equipment if you desire for easily affordable prices. At wowgold800.com, our highly trained staff are available on all US and Euro servers, [powerl eveling](http://www.wowgold800.com/) and [wow power leveling](http://www.wowgold800.com/), waiting to serve your World of Warcraft needs. Be it farming for gold, power leveling characters, grinding faction or honor points, contact us at [www.wowgold800.com](http://www.wowgold800.com/) today and speak to one of our representatives. You won't be disappointed!

---

### Post by pdq on 2008-09-11
go into the bios and set the drive with ubuntu on it to be the primary boot drive.

---

