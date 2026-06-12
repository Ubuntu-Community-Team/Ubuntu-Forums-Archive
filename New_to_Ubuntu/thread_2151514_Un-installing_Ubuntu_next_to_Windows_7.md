---
title: "Un-installing Ubuntu next to Windows 7"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by BNZBKK on 2013-06-04
I want to change My OS from 10.10 to 12.04 LTS. currently 10.10 is operating alongside Windows 7  and I've read about the possible difficulties to Windows in un-installing Linux
 
 
 1. What happens if I just 'Delete' the Linux folder in Windows 7  ?
 
 
 2. What happens if  I install 12.04 LTS first - then 'Delete' or uninstall 10.10

---

### Post by arpanaut on 2013-06-04
Is this a WUBI installation as you mention "the Linux Folder in Win7"

Or did you actually repartition your drive and install?
If installed within Win7 (wubi) then you can back up your data and uninstall from the add & remove programs in the control panel.

I will await your answer before going further.  There is a big difference about how to proceed.

---

### Post by BNZBKK on 2013-06-04
Thanks for your prompt response 'arpanaut' 

1. I'm not clear exactly what a WUBI installation entails but I certainly didn't repartition the drive when installing and there is a Linux 'folder' sitting in Windows

2. Data is already backed up and I can 'uninstall from the add & remove programs in the control panel.'


3. I've just read this and it presents no difficulties - [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by arpanaut on 2013-06-04
Then you are good to go uninstall from the CP then if you wish from the 12.04 iso reinstall with wubi.exe from the disk inside of windows or do a complete installation by booting into the live session and installing alongside windows.
You will need to resize your windows partition and have Ubuntu installed into the remaining free space.
Depends on how much free space you have available and how frisky you are feeling about repartitioning your drive.

---

### Post by BNZBKK on 2013-06-04
Thanks, I knew it had to be simpler than the dire threads I've been reading.

I'm certainly not frisky about resizing partitions as it's not my computer but there's 500GBs - most unused, so plenty of free space



I'll do it in a day or two and let you know.

Thanks again

---

### Post by arpanaut on 2013-06-04
wubi: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
and: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

VS.

Dual Boot: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and: [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

Hope this Helps

---

### Post by Mark Phelps on 2013-06-05
The amount of free space is NOT the issue; the issue is whether or not you have enough remaining partitions to create more for Ubuntu.

Don't just go charging into booting from the Ubuntu installer, resizing Win7 and forcing an install of Ubuntu.  That is a sure-fire way to render Win7 unbootable as a result!

If your SERIOUS about doing a side-buy-side instal of Ubuntu with Win7, read through the details below  BEFORE proceeding:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by BNZBKK on 2013-06-10
I've been an Ubuntu user for 6 or 7 years now and so far this is a disaster, I can't right click on anything, no options, flash player won't open, everything is slow, Opera only comes in one flavour and on and on and on - very buggy

Would I be better off deleting Wubi from Windows and letting Ubuntu install itself  ?  ..as 10.10 did with no problems

---

### Post by mastablasta on 2013-06-10
> **BNZBKK said:**
> I've been an Ubuntu user for 6 or 7 years now and so far this is a disaster, I can't right click on anything, no options, flash player won't open, everything is slow, Opera only comes in one flavour and on and on and on - very buggy

yeah because it uses 3D acceleration. you can still use gnome fallback or Unity 2D in 12.04. 

> 
Would I be better off deleting Wubi from Windows and letting Ubuntu install itself ? ..as 10.10 did with no problems

might be a better way. don't delete it. uninstall it. note that wubi i think has a size limit. it runs inside virtual drive. and is not supported in newer ubuntu version anymore. if oyu have enough ram then installing in virtual box might be simpler.
also have a look at Xubuntu. you never mentioned the system specs. do you maybe have a radeon 4xxx or 3xxx GPU?

---

### Post by BNZBKK on 2013-06-10
Thanks '**mastablasta'**, I've just installed the 10.10 desktop which enables a more fluid navigation.

Installing with-in 'Virtual Box' is possibly above my punching weight, you have to remember this is the **'Absolute Beginners Section'** so it has to be dumbed down !
 ..and system specs..2GB's Ram 500GB hard drive from, my memory, it's a nice little Acer EMachine. Guys like me don't need/want to know anything more but we want a better OS than Bill of Gates provides

  Basically it's this .. three years ago the 10.10 OS installed itself 'next' to Windows and worked fine but after a few years of serial abuse and acquired bugs a re-installation is acceptable.
 Now I've just installed 12.04 in Wubi but that seems to be a basic function ...so re-installing - 'next' to Windows 7 is the preferred alternative - but I don't want to screw up my sis's Windows 7. 
Do I let 12.04 install itself and hope that it will work (..after re-arranging the GRUB/startup ) as 10.10 did years ago ? 

Do I re-format the 'un-named' partition in/from Windows and hope 12.04 will install itself there  ?

  


 Thanks again '**mastablasta**, **'arpanaut' 'Mark Phelps'**   you're all getting me there  ..uhhmmm painfully


PS: Installation on my 100 % Ubuntu computer in Bangkok is no problem ..- re-format - and install - perfect.

---

### Post by mastablasta on 2013-06-10
> **BNZBKK said:**
> Installing with-in 'Virtual Box' is possibly above my punching weight, you have to remember this is the **'Absolute Beginners Section'** so it has to be dumbed down !
..and system specs..2GB's Ram 500GB hard drive from, my memory, it's a nice little Acer EMachine. Guys like me don't need/want to know anything more but we want a better OS than Bill of Gates provides


i thought it's difficult until i gave ti a try and mostly it consisted of clicking the next button and usign the porposed default values. anyway with 2GB ram and win7 ubutnu would be hard pressed, but lubuntu and even xubutnu will work ok : [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

> 
Basically it's this .. three years ago the 10.10 OS installed itself 'next' to Windows and worked fine but after a few years of serial abuse and acquired bugs a re-installation is acceptable.
Now I've just installed 12.04 in Wubi but that seems to be a basic function ...so re-installing - 'next' to Windows 7 is the preferred alternative - but I don't want to screw up my sis's Windows 7. 
Do I let 12.04 install itself and hope that it will work (..after re-arranging the GRUB/startup ) as 10.10 did years ago ? 


next to as in separate partition is easy and it is generaly safe. you should still backup the data just in case. partitioning always carries a small risk. which is why i haven't done it in my netbook (waiting for enough money to buy external HDD). another preparation is having iwndows 7 recovery disk (or just original disk) at hand in case you need to overwrite grub.

i have done it on a winPX once as i wasn't too worried about data in xp.

assuming you have part of disk available but formated you need to:
defragment the part you plan to resize at least two times - second one will be done fast (this should reduce chance of loosing any data to bare minimum)
then use the windows disk manager (used to be in accessories) to resize the partition. leave the part you want to use Ubutnu on unformatted. 

you will do the rest in ubuntu installer

boot ubuntu disk/USB (select it in BIOS as first boot device)
start the install and select to install it next to empty disk space. the rest is self explanatory and the usual Ubuntu install.

once you are finished grub menu should appear.

one thing if the 500GB disk is not the system disk you boot from but only data disk then you need to tell ubuntu installer where to put the grub (i.e. to your system boot disk).



once you are finished post back and we will deal with grub so that windows is first to boot.

---

### Post by BNZBKK on 2013-06-11
bump

---

