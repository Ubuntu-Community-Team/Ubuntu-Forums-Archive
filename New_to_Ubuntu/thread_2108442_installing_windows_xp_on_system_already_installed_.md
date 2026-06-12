---
title: "installing windows xp on system already installed with ubuntu"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by syednasirraza on 2013-01-24
i m having ubuntu 12.04 on my laptop...now i want to install windows xp and install later vmware and then ubuntu on vmware to explore it this way...
but when i insert bootable cd of xp,,,it tries to load but gives blue screen and halts and says there is some technical error,,may b virus or something,,,and it will discontinue to avoid any harm..... how to go on it
probably ubuntu has taken up all disk space with its file system since im having on ubuntu installed on my system...how to see it???how to manage disks???what to do
plz guide

---

### Post by arochester on 2013-01-24
Look at this: "How to dual boot Linux and Windows XP (Linux installed first) -- the step-by-step guide with screenshots" - [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by syednasirraza on 2013-01-25
thats an excellent detailed doc..i will try it now.....and will let u know...hopfuly it wil work for me
but what if i dont want dual boot ubuntu n xp,,,is there any way out if i want to completely remove ubuntu and install xp only????

---

### Post by arochester on 2013-01-25
Yes. Just run the XP install disk.

---

### Post by furything on 2013-01-25
If you are going to use vmware to explore ubuntu, I think that is what you are saying,
why don't you just install Oracle vmbox on  your ubuntu through synaptic package manger and then install ubuntu in the vm so you explore/play with.

Why bother with XP at all?

The description you are giving is that your xp disk is faulty or cannot deal with the hard ware without using the load additional drivers option. Windows will see the disk as non microsoft and give you the option to overwrite it anyway. You get a menu that says something along the lines of install to hard drive format as fat32 or ntfs.

Microsoft disk won't repartition the disk for you to share with ubuntu (it sees it as the enemy). So follow the guide which is very good or just install vm box now on your existing ubuntu (far easier)

---

### Post by offgridguy on 2013-01-25
> **arochester said:**
> Look at this: "How to dual boot Linux and Windows XP (Linux installed first) -- the step-by-step guide with screenshots" - [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
This is an excellent looking guide,i see though that it was last
updated in 2009,so some things may have changed.

---

### Post by Mark Phelps on 2013-01-25
An initial problem you will have trying to install XP is that it does not recognize Linux filesystems.  And, since you can't shrinka partition while you are using it, you can't shrink the Ubuntu partition while it is running.

You will have to boot from an Ubuntu LiveCD or LiveUSB, go to the desktop and open GParted (Gnome Partition Editor).  That will allow you to shrink the partition to make room.  

You can then also create a new NTFS partition for XP, or you can do that using the XP installer.

---

### Post by syednasirraza on 2013-01-26
> **Mark Phelps said:**
> An initial problem you will have trying to install XP is that it does not recognize Linux filesystems.  And, since you can't shrinka partition while you are using it, you can't shrink the Ubuntu partition while it is running.

You will have to boot from an Ubuntu LiveCD or LiveUSB, go to the desktop and open GParted (Gnome Partition Editor).  That will allow you to shrink the partition to make room.  

You can then also create a new NTFS partition for XP, or you can do that using the XP installer.

PROBABLY THATS MY PROBLEM...infact when i try to install xp,,i cant since xp does not recognize linux filesystem,,,furher i cant shrink partition while using ubuntu...so now hint for me is to boot from ubuntu cd and then trying to use Gparted from desktop to shrink disk and make space available for xp....thts what i will b trying now...wish me good luck...
I HOPE BY BOOTING FROM UBUNTU CD,,, I WILL BE EASILY ABLE TO FIND WAY TO REACH DESKTOP AND LINK TO Gparted...
thnx all others for informative replies

---

### Post by oldfred on 2013-01-26
The other issues are that Windows only boots from a primary partition (sda1 thru sda4) and it has to be formatted NTFS with the boot flag. Or you have to have free space and available primary partition for it to install to.

---

### Post by monkeybrain2012 on 2013-01-26
> **syednasirraza said:**
> i m having ubuntu 12.04 on my laptop...now i want to install windows xp and install later vmware and then ubuntu on vmware to explore it this way...


Why don't you just install xp in vmware or virtualbox? XP works better in vbox than Ubuntu 12.04 in Vbox anyway because of Ubuntu's 3d desktop.

---

