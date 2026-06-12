---
title: "Unable to Install from CD"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by haggar47 on 2011-10-05
I am new Ubuntu 11.o4.  Working fine with a dual boot of WindowsXP, then just crashed.  I used DOS FDISK and FORMAT to create a single partition.
 
I have downloaded three ISO copies to a CD (700 MB), only one begins to boot, then dies--black screen with cursor.  I tried all options using F6, to no avail.
 
Computer Specs:
 
MSI K8M NEO-V motherboard
AMIBIOS V3.31A
512 MB DDR 400
AMD ATHLON 64 BIT, SOCKET 754
VIA CHIPSET K8M800
VT CHIPSET VT8237
 
I believe I have read all threads pertaining to UBUNTU 11.04 Install and Boot.
 
What is the MD5SUM??   Is it downloaded with the ISO file or is it a separate download?
 
Have I downloaded the wrong file?
 
Please Help!  I have spent approximately 30 hours to resolve this issue before trying this thread.
 
Thanks to all who can help!

---

### Post by coffeecat on 2011-10-05
> **haggar47 said:**
> What is the MD5SUM??   Is it downloaded with the ISO file or is it a separate download?

This will tell you about md5sums:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And here is a list of Ubuntu md5 hashes:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

By the way, using DOS fdisk will create a partition, but it will probably be a primary one, and formatting it with a Microsoft utility will format it with a Microsoft filesystem. To install Ubuntu, it will need to be reformatted with a Linux filesystem. Once you get the Ubuntu live CD working, you'll find the partitioner Gparted on it. It has all the features you will need, or the installer can do partitioning for you, including creating logical partitions which give you more flexibility.

---

### Post by haggar47 on 2011-10-05
I downloaded the MD5SUM to the boot CD and now I cannot boot at all from the CD.
 
Is there a ubuntu format file that can be downloaded to a CD?
 
I read the links you provided, however, I do not understand!  Too used to DOS!

---

### Post by coffeecat on 2011-10-05
> **haggar47 said:**
> I downloaded the MD5SUM to the boot CD and now I cannot boot at all from the CD.
 
Is there a ubuntu format file that can be downloaded to a CD?

I'm not quite sure what you mean by those.

You download the ISO file to your hard drive - to any convenient temporary location. Then you check the md5 hash of the downloaded ISO to be sure that it was not corrupted during download. If it passes the md5sum test, you then burn the ISO to CD to create a bootable CD. You need to burn as image with a burning application, otherwise you get a CD with one huge ISO file on it, which won't boot at all. Here's another link for you:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Don't hesitate to ask any more questions if anything is not clear. :)

**EDIT**: by the way, are you using the onboard VIA graphics on your motherboard or do you have a PCIe/AGP card?

---

### Post by haggar47 on 2011-10-05
I cannot get any of the three downloads to CD to install!
 
Is there a Ubuntu format driver?  Should I just undo the FDISK and FORMAT commands and leave an unformatted drive!
 
Thank you for your help!  Unfortunately, I do not understand much of the terminology!

---

### Post by coffeecat on 2011-10-05
I think you are muddling some things up. Forget the internal hard drive and formatting a partition for now. Forget installing Ubuntu to the hard drive for now as well. The first thing is to get a bootable Ubuntu CD which can boot into a usable live desktop session. Did you burn the ISO image to CD following the instructions in the link I posted? Did you change the boot order in the computer BIOS so that it boots from the optical drive first?

---

### Post by viperdvman on 2011-10-05
Windows programs like Nero or Roxio can usually burn ISO images to CD's with no problems. Don't ask me about any open-source ISO image burner or CD-burning programs as all the ones I have on my Windows installation are proprietary.

Hope you get it to work

---

### Post by AskTell on 2011-10-05
download poweriso from [http://www.iso-file.net/PowerISO48.exe](http://www.iso-file.net/PowerISO48.exe) found at [http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm) once you've installed this program you'll be able to open the iso image and use poweriso to burn it to your disc

[http://www.youtube.com/watch?v=s5y-4_hkXkA](http://www.youtube.com/watch?v=s5y-4_hkXkA) heres a howto video for burning iso's using poweriso

its pretty simple to use, good luck!

---

### Post by haggar47 on 2011-10-05
Will your suggested ISO burner program automatically unzip the files while it is burning or do I have to some other unzip program first?
Thank your for your reply!

---

### Post by AskTell on 2011-10-05
when your burning an iso image with poweriso it automatically unpacks the image

---

### Post by haggar47 on 2011-10-05
Just burned another cd--continues to go out to la la land?
Pleassssssssssssssse help!  I burned 6 cds and none will install.  I downloaded the AMD 64 ISO file?
 
Any more suggestions???   I am ready to give up even though when it ran fine with XP it appeared to have great features--just crashed and wouldn't restart..  Just very unfamiliar with the terminology.
 
Thank you for your patience and understanding!

---

### Post by haggar47 on 2011-10-05
Just started to install--segmentation fault.............

---

### Post by dFlyer on 2011-10-05
What caused windows to crash? Can you boot to a live desktop? You say you formated your hard drive, did you reinstall windows? who is creating your boot disk and what OS are they using? I'm just trying to understand what is going on.

---

### Post by owiknowi on 2011-10-05
first of all: don't panic (it's just a computer) ;)

second: since you formatted your disk, i would start by trying to re-install windows xp from the original installation cd as shipped with your pc.

this way you can see if there's somethings wrong with your hardware. if that works we'll take the next step.

---

