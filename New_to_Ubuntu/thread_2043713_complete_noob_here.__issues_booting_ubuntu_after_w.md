---
title: "complete noob here.  issues booting ubuntu after win7 reinstall"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by Octoborg on 2012-08-17
Hi. I am very new to Ubuntu but am very excited by what I have seen!  I have browsed through these forums looking for solutions to my problem similar to mine, but am having a hard time applying them. 

A few days ago I decided I wanted to dip my feet into linux and boldly download ubuntu without have any idea of I was getting myself into.  I attempted to partition my hard drive through LTS 12.04. so I could also use windows 7(64x).  This ended up back firing, and I lost all of my data, and neither OS would boot.  Not discouraged, I decided to try again - I popped in my reinstall disc for windows 7 and immediately reinstalled ubuntu, this time opting to overwrite win 7 entirely.  

This worked well for a while and I got to play around with a lot of the awesome software in the software center.  Unfortunately I was having some trouble running skyrim through wine (invalid pathway error) so I decided it would be simpler to install windows 7 on a partition for the sake of convenience while I got more comfortable with Ubuntu.   I created a partition in ubuntu through gparted and installed windows 7 on it via the installation disc.  Now ubuntu will not boot, and I was hoping to get some help regaining access to my ubuntu partition, without losing windows 7.   How should I approach this problem from the windows 7 end?  

I get the following error when selecting Ubuntu on the Windows Boot Manager

Windows failed to start.  A recent hardware or software change might be the cause. To fix the problem:

1. Insert the windows installation disc and restart your computer.
2.  Choose your language settings, and then click "Next."
3. Click "repair you computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \ubuntu\winboot\wubildr.mbr

Status: 0xc0000001

Info: The selected entry could not be loaded because the application is missing or corrupt.

As I said earlier I am extremely new to Ubuntu but would love to learn to use it harmoniously with windows.   I have spent the better part of two days trying to figure out a solution, but this is all still very new to me, as you can easily tell!   I would like to find a way to regain access to the apparently corrupt ubuntu partition.  The filesystem used by my windows is ntsf and my ubuntu is on ext4.. I'm not really sure what other information is needed to solve this but eagerly await a response!  Thank you!

---

### Post by NikTh on 2012-08-17
Hi , 
It is Ok. Experiments make you more experienced :) 

You had a Wubi installation I understand . Now wubi corrupted and you cannot boot in Ubuntu. 
First thing , go to Control Panel and try to find something with Ubuntu or wubi , if you find it , delete it. Like any other application in windows. 

Then do a defrag in hard disk with windows defrag tool. 
After that see this video tutorial on how to install Ubuntu alongside (and not inside) windows on the same hard disk. 
[http://www.youtube.com/watch?v=LokDqte3sA4](http://www.youtube.com/watch?v=LokDqte3sA4)

This is the simplest method. No advanced options or partitioning.. etc.
Follow above steps and you will be fine.
Thanks and Welcome to UbuntuForums.org

---

### Post by Kickinthedoor on 2012-08-17
Sorry to hear you lost all of your data, anytime you creat a partition you should back up anything important. Any way for a long time i only used ubuntu but when i signed up for netflix i needed a windows os to watch it so i asked for some help and i was told i should install windows 7 first and then create a partition for ubuntu. If i recall its a problem with the boot loader since windows doesnt play well with others. So un fortunatly i think your going to have to start over again this time with win 7 as the first instal. good luck and keep us posted

---

### Post by Octoborg on 2012-08-17
Actually I didn't install Wubi.  Is there any way to restore the data from my ubuntu install?

---

### Post by NikTh on 2012-08-17
> **Octoborg said:**
> Actually I didn't install Wubi. 

> **Octoborg said:**
> 
File: \ubuntu\winboot\wubildr.mbr

Status: 0xc0000001

Info: The selected entry could not be loaded because the application is missing or corrupt.

Hi, 
Above says you had a wubi but now is corrupted. 

> **Octoborg said:**
>   Is there any way to restore the data from my ubuntu install?
The easy method is to boot from a LiveCD / Usb and open nautilus from terminal like this
```
gksudo nautilus
``` then you must find you files and copy them somwhere else (e.g: external usb or hdd)
Thanks

---

### Post by Octoborg on 2012-08-17
Ah, I stand corrected!  I will try your suggestion, thank you.

---

### Post by lamarkia on 2012-08-17
> **Kickinthedoor said:**
> If i recall its a problem with the boot loader since windows doesnt play well with others. So un fortunatly i think your going to have to start over again this time with win 7 as the first instal. good luck and keep us posted

I found this to be true when trying to install Linux Mint on a Win7 machine. You need to install Windows and partition from there, then install Ubuntu on the partition.

When you restart, it will automatically boot into Windows. You need to edit a file in Ubuntu to bring up the grub menu (choice of OS to boot up at the start). Have a read of [[COLOR="Blue"]_this_[/COLOR]]("http://hlug.co.uk/desktop-linux-f39/change-default-boot-order-for-grub-2-in-ubuntu-12-04-t165.hlug")

---

