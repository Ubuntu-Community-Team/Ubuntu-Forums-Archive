---
title: "Question about dual boot"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by trolol on 2012-01-31
Hi first off sorry if this is a dumb question and I know there are threads and guides about this already but I find them all very hard to understand so I just need a simple answer.

1.When you put in a live CD or live usb you get the option that says install. When you click on this it gives you another option to install normally or install with windows. If i click install with windows or whatever it says. Will it do all the work for me and install it with windows without me having to do anything, or will I have to do some stuff like partitioning etc on windows before I install??

2. If so how much space will I need for Lubuntu?

3. Also when I install with windows will my hdd be cleared, should I put everything on an external hdd? 

4.Is there a risk of my hdd going corrupt?

5. Does having a really low ram mean installing only one os is faster than a dual boot or does it not matter because only one will actually be used?

6. Does compiz and other customization like themes etc work normal on lubuntu or are there limitations?

So yeah please just a simple answer for each question and sorry if any of these are dumb I really need to know ty for any help, cant wait to get started on ubuntu!

---

### Post by chughes27 on 2012-02-01
When you install from live CD/USB, the installer will do everything for you. No need to partition or anything like that. When you install alongside Windows, it will keep all of the files on you hard drive. Ubuntu will just be created in its own separate folder. Dual booting won't affect your RAM, as only one OS will be used at one time. 

As to your Lubuntu questions, I don't know, I'm not really familiar with Lubuntu.

---

### Post by Rodney9 on 2012-02-01
I have been using Lubuntu 11.10 for a few months and have a lot photos etc and I have used 36GB, so I guess 30GB would be plenty. Lubuntu will fit on a 4GB USB

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by raja.genupula on 2012-02-01
> 
1.When you put in a live CD or live usb you get the option that says install. When you click on this it gives you another option to install normally or install with windows. If i click install with windows or whatever it says. Will it do all the work for me and install it with windows without me having to do anything, or will I have to do some stuff like partitioning etc on windows before I install?? 

If you select that option it will skip the partition step and remaining details and remaining steps as normal . 

> 2. If so how much space will I need for Lubuntu?

I heard its a light weight Ubuntu but what ever it is minimum Ubuntu need 4.5 GB i think . but better to give more . depends upon free space of your hard disk . The latest version need 384 MB of RAM (thats recommended) for Graphical environment
> 3. Also when I install with windows will my hdd be cleared, should I put everything on an external hdd? 

taking backups is always a good idea while doing new installations and upgrades of new distro . But 99.99%(ofcourse 100% to me ) installation not going to failed . but make sure that no changes to windows partition while doing installation (except install next to windows i mean that first option) 

> 4.Is there a risk of my hdd going corrupt?
no 

> 5. Does having a really low ram mean installing only one os is faster than a dual boot or does it not matter because only one will actually be used?


For Lubuntu we need minimum 384 MB but better to have 512 MB  and for Xubuntu minimum 512 MB but better to have 1 GB and 2GB or > 2GB for Kubuntu and Ubuntu
> 6. Does compiz and other customization like themes etc work normal on lubuntu or are there limitations?
sorry man i am not having any idea with this


Hope that helps .

---

### Post by trolol on 2012-02-01
> **raja.genupula said:**
> If you select that option it will skip the partition step and remaining details and remaining steps as normal . 

Sorry I didnt quite understand what you meant by that, can you just simplify your answer a little more? Does what you said mean I dont have to do anything at all and the install will just do it all for me?

thanks for everything else though

---

### Post by raja.genupula on 2012-02-01
actually we have to give a partition to Ubuntu for installation . but if you select that option it will choose the partition automatically . your job simply give a "next"

But selecting partition is not a big deal . if you have a empty partition then you have to select it and click at add and then select ext4 and mount point as "/" .if any unwanted partition then click at delete and repeat above process .

---

### Post by trolol on 2012-02-01
> **raja.genupula said:**
> actually we have to give a partition to Ubuntu for installation . but if you select that option it will choose the partition automatically . your job simply give a "next"

But selecting partition is not a big deal . if you have a empty partition then you have to select it and click at add and then select ext4 and mount point as "/" .if any unwanted partition then click at delete and repeat above process .

okay thanks bro this helped me alot

---

### Post by raja.genupula on 2012-02-01
you welcome man . do the installation and if you got any problem then we are here for  you . 

All the best .

---

### Post by Mark Phelps on 2012-02-01
I didn't notice what version of Windows you're using, but if it's Vista or Win7, do NOT use the option of side-by-side, using the slider to resize the Windows partition.  These OS's are very finicky about their filesystems being messed with from "outside". They can result in filesystem corruption, rendering Windows unbootable as a result.

Instead, boot into Vista/Win7 and use the Disk Management utility to shrink the windows OS partition.

Then, when you boot into the Ubuntu installer, you have to select the empty space for the partitioning.

---

