---
title: "Will corrupt window affect ubuntu too?"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by shri_ved on 2011-11-04
I am completely new to linux & have been using windows for long time. I have recently installed Ubuntu with wubi so I can uninstall it if I find it unsuitable for me. I want to know that if window get corrupted, will it also corrupt Ubuntu which I have installed inside Window 7?

Thanks.

---

### Post by dileepm on 2011-11-04
Well if you are completely unable to access u r windows, then obviously u may not have access to WUBI Version. I prefer to install it as whole to enjoy Ubuntu. The dual boot will not affect other if one is corrupt(at least most of them don't)

---

### Post by Paqman on 2011-11-04
> **shri_ved said:**
> I want to know that if window get corrupted, will it also corrupt Ubuntu which I have installed inside Window 7?


Possibly, it depends on what happens to Windows. Wubi installs Ubuntu into a file located on the Windows filesystem. If the Windows filesystem gets corrupted (which is pretty unlikely) then Ubuntu would be affected. If the corruption just affected Windows system files and not the underlying filesystem, then Ubuntu would be fine.

---

### Post by kellemes on 2011-11-04
I would setup a dual-boot system.. If you want to get rid of Ubuntu you only have use you favorite partition-editor to delete it's partition(s) and expand your Windows-partition to use the freed space. Also you need to restore your Windows-bootloader..
There are a lot of threads that explain how to do this..

---

### Post by sanderd17 on 2011-11-04
Wubi is perfect for a longer testing period (up to 6 months).

But if you use Wubi too long, there's a chance where you forget to maintain your Windows installation and where your installation just stops working.

So my advise is: try with Wubi first, until your installation crashes* or until there is a new version of Ubuntu. And then do a real dual boot installation.

(*) Linux newbies most of the time forget the power you get in Linux. You are allowed to do everything (including stupid things). Linux might warn you, but it won't stop you.

---

### Post by riverabove on 2011-11-04
Yup..maybe right now is the time for you to install Ubuntu physically on your PC. And I agree too with the others, set up the dual-boots system. Although you install Ubuntu on different partition with the Windows, you can browse your files on the Windows hard drive partitions (this is one point from Ubuntu that can impress me ;) as UbuntuNewbie. But in the opposite, windows can't browse the Ubuntu partition).

Last several days ago, my wife wanted to use my windows but failed when booting. It's because there is a lost file from the 'system32'. Of course it won't disturb my Natty because..as you can see, they are installed on different partitions.

---

### Post by kellemes on 2011-11-04
> **riverabove said:**
> But in the opposite, windows can't browse the Ubuntu partition).


Yes it can, there are some drivers available for that..
Edit: for example [Ext2Fsd]("http://www.ext2fsd.com/")
As far as I understand ext4 is readonly.

For sharing files between os's it's easiest to create a seperate fat-formatted partition so you have default read/write access from both os's.

---

### Post by Paqman on 2011-11-04
> **kellemes said:**
> 
For sharing files between os's it's easiest to create a seperate fat-formatted partition so you have default read/write access from both os's.

NTFS works for this too, and doesn't have some of FAT's limitations.

---

### Post by 3rdalbum on 2011-11-04
A basic rule of thumb is that, if Windows won't boot, then Ubuntu won't either. This is because if Windows fails to boot, it leaves its filesystem in an inconsistent state, and Ubuntu's NTFS support won't touch an inconsistent NTFS filesystem for fear of damaging it further.

---

### Post by shri_ved on 2011-11-04
> **kellemes said:**
> I would setup a dual-boot system.. 


If I would also prefer to go for dual boot system, then would I require to reinstall Win 7 again for keeping some part of hard disk free so I can use it for Ubuntu installation? because it will cause me to save the complete data which is present on the hard disk thus I would not loose any data in re installation process. I have some partition completely empty. Can I use it for installing Ubuntu for dual boot purpose without going through Win 7 re installation?

---

### Post by mikechant on 2011-11-04
> If I would also prefer to go for dual boot system, then would I require to reinstall Win 7 again for keeping some part of hard disk free so I can use it for Ubuntu installation?

No, you don't need to reinstall Windows to switch from wubi to dual-boot.
I would do the the following:
[LIST=1]
[*]Back up any Ubuntu files you want to keep from your existing wubi install if necessary
[*]Uninstall the Ubuntu wubi install (I believe you just use Windows add/remove programs facility or whatever it's called now)
[*]Use the Windows disk utilties to defrag the windows partition several times (probably 3 times will do)
[*]Use the Windows disk utility to shrink the main windows partition enough to make space for Ubuntu
[*]Now boot from the Ubuntu Live CD/USB and install using the 'use available free space' option
[/LIST]

It's strongly recommended that you do not use Ubuntu's installer option to shrink the Windows partition since this can make Windows unbootable.

---

### Post by riverabove on 2011-11-06
[QUOTE=kellemes;11423884]Yes it can, there are some drivers available for that..
Edit: for example [Ext2Fsd]("http://www.ext2fsd.com/")
As far as I understand ext4 is readonly.

Owh..that's a new good info for me..:) thanks a lot..

---

### Post by Mark Phelps on 2011-11-06
Problem is, as far as I remember from my last install, there is no "Use available free space" option anymore in the Installer.  You have to go into Manual Partitioning -- and there is where folks make mistakes and accidentally erase their Windows installations.

---

### Post by shri_ved on 2011-11-10
> **mikechant said:**
> No, you don't need to reinstall Windows to switch from wubi to dual-boot.
I would do the the following:
[LIST=1]
[*]Back up any Ubuntu files you want to keep from your existing wubi install if necessary
[*]Uninstall the Ubuntu wubi install (I believe you just use Windows add/remove programs facility or whatever it's called now)
[*]Use the Windows disk utilties to defrag the windows partition several times (probably 3 times will do)
[*]Use the Windows disk utility to shrink the main windows partition enough to make space for Ubuntu
[*]Now boot from the Ubuntu Live CD/USB and install using the 'use available free space' option
[/LIST]

It's strongly recommended that you do not use Ubuntu's installer option to shrink the Windows partition since this can make Windows unbootable.

Thanks mate,

I had four partition (of 100GB each)& one of which I freed up (by Window disk manager) & uninstalled ubuntu. Then in installation process I assigned this free space of 100 GB for ubuntu in which I assigned 88GB for root & remaining 12GB for swap in manual file creation mode. I didn't know how to create other files therefore I only created "/" & "swap". In installation it has created other file itself.Os is working fine. Now has it achieved dual boot? Is it now completely free from window?

---

