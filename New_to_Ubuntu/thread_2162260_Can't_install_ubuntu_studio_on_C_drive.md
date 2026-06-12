---
title: "Can't install ubuntu studio on C drive"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by Tyler Zambori on 2013-07-13
hi,

I want to install it alongside windows on my C drive. I am not given that choice, if I choose
to install it alongside windows. It wants to install on my D drive ,and I don't want it to go there.

How can I install it in my C drive alongside windows? 

Thanks!

---

### Post by Mr.Dunham on 2013-07-13
I'm not really sure, but I think it's because you first need to create a new partition to install it on that drive, the installation won't let you install on your C drive because Windows is already on it. Still, the new partition will be treated as a new drive, though.

---

### Post by QIII on 2013-07-13
Hello --

Are you trying to install using Wubi?

Thanks.

---

### Post by Tyler Zambori on 2013-07-13
> **QIII said:**
> Hello --

Are you trying to install using Wubi?

Thanks.

yes, I downloaded ubuntu studio 13, burned it to dvd, then
tried to install. Wubi is the file listed as the application.

Should I be using something else?

---

### Post by newb85 on 2013-07-14
Before installing, you should understand your install options.

Ubuntu is designed to operate independently of Windows.  The DVD is bootable - you can boot your machine from the DVD instead of the hard drive and then install it on its own partition(s).  (Note, Windows refers to partitions as drives, which can be a bit confusing.  Most likely, your C: and D: "drives" are just partitions of one physical drive.)  

Wubi is an alternative to that traditional dual-boot setup.  Instead of booting from the DVD, you can run the Wubi installer from within Windows.  Also, instead installing Ubuntu on it's own partition, it creates a virtual hard drive on one of your Windows partitions and installs it there.

There are some here on the forums who recommend Wubi, but most (including me) would discourage it.  If you're really serious about using Ubuntu, a traditional install is more stable.

---

### Post by Tyler Zambori on 2013-07-14
Ok, no my C and D drive are not most likely partitions of one physical drive. They are physically separate hard drives.
yes I agree that a traditional install is better. That is what I want, and that I'm what I'm trying to do.

My D drive has a whole lot of content on it, and it makes me nervous to let ubuntu install there -
I have no idea what might happen to all that content.   The D drive is also running out of room.

I really do not want to run wubi from within windows.

---

### Post by grahammechanical on 2013-07-14
You still do not tell us what version of Windows you have and what version of Ubuntu you want to install.

The installer is, most likely, choosing the D: drive because there is no space on the C: drive. It could be that the C: drive is already partitioned into four primary partitions (drives) and four is the maximum allowed primary partitions. Or it could be that Windows has set the C: drive as a dynamic disk which the installer can not read as the dynamic disk is a specification that Microsoft keeps secret.

Could you run a Windows utility that shows your drives and take a screenshot and post it here? It is better that we see your disks layout and then you may get helpful advice and not good advice that damages things because you did not provide accurate information.

Regards.

---

### Post by Tyler Zambori on 2013-07-14
I have windows 7 and am trying to install ubuntu studio 13.  I have plenty of room on my C drive.

I do not have 4 primary partitions on the C drive.  My statements are accurate. 

I have gone ahead and created a second partition on the C drive.  I named this new
partition on the C drive as E. 

In Disk management in widows, the C partition is described as:

healthy (system, boot, page file, crash dump, primary partition)

The E partition is described as: healthy (primary partition)

The D drive is still the same as it ever was, and is still a separate hard drive
with no partitions. 

Ok now that I have done that, I want to install ubuntu on the E partition
which is on the same drive as the C partition. 

So I want to work up to my next question: when I click on the "choose something else
option,"   (that is, not installing alongside windows in the manner that ubuntu chooses
by default, and also not installing it within windows), what device do I choose for
boot loader installation?  

I figured out that the new E partition is listed as:

/dev/sda2 (ntfs)

I know this by looking at the amount of HD space available.

So what device would I choose for boot loader installation?

I tried both:

/dev/sda/

and

/dev/sda2

And the result was a message saying:

No root file system is defined. Please correct this from the 
partitioning menu. 

So where is this partitioning menu? I see no such menu.

I am *sure* they don't want me to choose:
/dev/sda1/ windows loader, as that is the windows loader!

So how do I set this up so I can choose the correct place for boot loader 
installation? And which is the correct one? And where is this partitioning
menu?

Thanks!

Ps: it still does not work. ubuntu still wants to install on the D drive by default
when I choose the "install alongside windows" option.  The D drive has no
partitions and is getting short on space. Unlike my c drive which has plenty of space.
Many gigabytes plenty of space.

---

### Post by newb85 on 2013-07-14
If you're doing a traditional install (booting from the DVD to install), you'll have to delete the new NTFS partition you've created and put an EXT4 partition in its place.  (Ubuntu won't install directly to NTFS.)  You can do this once you get to the "Do something else" part of the installation.  When you create the EXT4 partition, set its mount point as "/".  The bootloader should be on whichever hard drive your BIOS is set to boot from by default (most likely sda).

---

### Post by QIII on 2013-07-15
If you are concerned about overwriting the files on your "D: drive" you can physically unplug it while you are installing Ubuntu to avoid making a frustrating or costly mistake.

---

### Post by Tyler Zambori on 2013-07-16
> **newb85 said:**
> If you're doing a traditional install (booting from the DVD to install), you'll have to delete the new NTFS partition you've created and put an EXT4 partition in its place.  (Ubuntu won't install directly to NTFS.)  You can do this once you get to the "Do something else" part of the installation.  When you create the EXT4 partition, set its mount point as "/".  The bootloader should be on whichever hard drive your BIOS is set to boot from by default (most likely sda).

It worked! Mostly!  Thanks newb85!

The thing is, I got a message about swap space: 

"You have not selected any partitions for use as swap space.  Enabling swap space
is recommended so that the system can make better sue of the available physical
memory, and so that it behaves better when physical memory is scarce.  You may 
experience installation problems if you do not have enough physical memory."

So how do I enable swap space? 

Thanks!

---

### Post by newb85 on 2013-07-17
SWAP space would be an extra partition you add (formatted as SWAP).  It's optional.  If you add it, it's recommended that you make it between one and two times the size of your RAM.  If you have the system working already, I would suggest you run it as-is for a while.  You can always add SWAP later.  SWAP isn't of any serious benefit unless you find yourself using all of your RAM or you plan on using Hibernate.  (Hibernate is disabled in Ubuntu by default.  It can be enabled, but it doesn't work on a lot of hardware setups.)

If you need to add SWAP later, boot from your DVD/USB and select "Try Ubuntu".  Open Gparted, shrink one of your partitions and add the SWAP partition.

---

### Post by su:bhatta on 2013-07-17
Welcome to Ubuntu family...

Any audio work you want to do with Ubuntu Studio?

Refer to this page for starters:
[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)

---

### Post by 3rdalbum on 2013-07-17
Swap is not important, don't worry about it.

---

### Post by Tyler Zambori on 2013-07-17
Thank you everybody!

---

