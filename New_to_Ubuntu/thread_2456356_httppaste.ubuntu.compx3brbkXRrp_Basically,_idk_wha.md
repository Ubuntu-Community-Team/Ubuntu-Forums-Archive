---
title: "http://paste.ubuntu.com/p/x3brbkXRrp/ Basically, idk what am I doing and I need help"
date: 2021-01-10
forum: New to Ubuntu
---

### Post by xav++ on 2021-01-10
I have a dual-boot scheme ubuntu 18.04 lts and w10 idk 2017 update or at least I used to have it

So, I'm gonna start saying that I live in Venezuela, just to contextualize my sorrow (lol), and power outages are very common and during one of them my laptop was booting up so w10 died and since I don't have proper internet I couldn't fix it right away, and yada yada yada trying to fix it I got frustrated and quit on w10 and kept ubuntu and updated it to the latest version available 21.04 or 20.10 i don't remember

a couple of months later I needed w10 and after backing up all my data and booting up a flash drive when i went to try to boot it I unintentionally eliminated the boot of Ubuntu, leaving me w/any working OS and lost part of the data I had backed up 

miraculously, my brother had ubuntu 20.04 so I got back on the horse and try to install w10 booting the flash drive again but this time I did it correctly, but when I finally made to the installation process I find out that my disk scheme was MBR and I needed GPT to install it using UEFI, so I used gdisk but I just changed the partitions from MBR to GPT and exit it, but when I did it I lost the boot of ubuntu again, but I was able to finally install w10, so I burned yet again the same flash drive w ubuntu 18.04 and run the  boot repair tool just to confirm that i didn't have recommended repair option available and under the advance settings there is the repair file system option but I'm afraid that might damage my w10 installation and I don't want that so I'm following the advice the tool gave me and doing this thread just to drain a little bit my frustration 
I might just need to install ubuntu from scratch all over again and get over with it, but idk this is some sort of last shot to recover whatever is left of my ubuntu install

thank you for reading this, for your time and your help

and sorry for my English I'm just tired 

Hope you have a good day.

---

### Post by QIII on 2021-01-10
Do not use the Ubuntu Forums as a political soapbox.  Clear?

---

### Post by yancek on 2021-01-10
Read the information at the link below as it is the Ubuntu official documentation al dual booting with windows 10/Ubuuntu?  Don't try to install Ubuntu before reading it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> I find out that my disk scheme was MBR and I needed GPT to install it using UEFI, 

Correct as you will see when you read the pages at the link above.  Windows won't instasll UEFI on a non-GPT disk.

As far as boot repair, the best option users who don't understand the boot process can select is the Create BootInfo Summary option.  When you run that from boot repair, you will get a link at the end which you can post here and it should provide enough information for someone to assist.

---

### Post by grahammechanical on 2021-01-10
May I add something?

With the mains supply unreliable, I would not want to be in a situation where I had to upgrade an out of life Ubuntu to a newer release before I needed to. If you have to re-install Ubuntu then install 20.04. That will be supported until April 2025. Whereas, Ubuntu 20.10 will reach end of life July 2021. 

And as for Ubuntu 21.04, that has not yet been released. It is in development and receives updates almost every day. With an unreliable mains supply I would not run a development release of Ubuntu as my only release of Ubuntu. I do not do that now and I live in London, England. It has been a long time since we experienced a power cut. Burst water mains are a different matter. We had a burst water main last year and also one today which has been fixed within the last hour.

Such is life. Regards

---

