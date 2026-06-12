---
title: "Installing Linux on a hard drive before installing the hard drive..?"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Old Pink on 2012-02-05
I have a hard drive (6GB) out of my laptop that I've loaded onto my desktop in a USB environment. Currently it's just FAT32 and functioning as an external hard drive.

I'm wondering if there's any easy way to install Ubuntu to this hard drive, then put it in an old Dell laptop I've got an fire it up? (The laptop doesn't have a CD drive, and won't boot from USB)

Ubuntu is the priority, but if there's any easier/smaller/made-for-purpose distributions anyone knows about, I'm happy to try them.

If I could boot from an Alternative LiveCD, mount the 6GB usb, install Ubuntu, put the hard drive in the laptop and turn it on, that'd be the dream - but I know nothing is that easy. Also if I could do the install to the hard drive from within XP, that'd be nice too, save accidentally messing up anything on this computer.

---

### Post by Cheesemill on 2012-02-05
> **Old Pink said:**
> If I could boot from an Alternative LiveCD, mount the 6GB usb, install Ubuntu, put the hard drive in the laptop and turn it on, that'd be the dream - but I know nothing is that easy.

It's that easy.

Simply fire up the Live CD (you could use the Alternate CD but there really is no point) and install as usual, just make sure you install GRUB onto the USB drive rather than your PC's main hard disk.

I'm not sure of the system requirements but 6GB would be pushing it, that might not be enough space when you start installing applications.

---

### Post by Old Pink on 2012-02-05
> **Cheesemill said:**
> It's that easy.

Simply fire up the Live CD (you could use the Alternate CD but there really is no point) and install as usual, just make sure you install GRUB onto the USB drive rather than your PC's main hard disk.

I'm not sure of the system rewuirements but ^GB would be pushing it, that might not be ebough space when you start installing applications.

Cheers for the help. A couple quick points:

[LIST]
[*]How do I make sure I install GRUB to the USB drive, and not this computer? I really don't want to mess anything up on this PC.
[*]I will most likely be using the alternate CD, just because this computer is pretty slow. If the USB drive doesn't automatically mount, how can I mount it? 
[*]Is there any way to do this from a virtual machine? Just to save accidentally screwing anything up with GRUB.
[/LIST]

---

### Post by Cheesemill on 2012-02-05
To make absolutely sure you install GRUB to the correct place you can disconnect the computers internal drive. If you don't want to do this then just make sure you take a look at the advanced options when it comes to installing the bootloader. If you're using the alternate CD then it's more obvious than if you use the Live CD.

You don't need to mount the USB drive, in fact the installer will unmount it when you try to do the partitioning as you can't partition a mounted drive.

It is possible to use a VM but this is usually more effot as with VirtualBox you first have to set up USB passthrough, and you wont be able to check if has installed properly with a VM as VirtualBox doesn't allow booting from USB devices.

---

### Post by Old Pink on 2012-02-05
I'm going to have a play around with my alternate CD ISO and Microsoft Virtual PC 2007. Failing that, I'll boot from my physical alternate CD and give it a pop. 

Thanks again, I'll keep you informed.

---

### Post by Old Pink on 2012-02-05
OK so Virtual PC won't recognize USB drives, but it looks like I'll be able to crack it with VMWare.

---

### Post by Bodsda on 2012-02-05
> **Old Pink said:**
> OK so Virtual PC won't recognize USB drives, but it looks like I'll be able to crack it with VMWare.

Can't comment on Virtual PC, but VirtualBox can detect usb drives after you install the guest additions.

Bodsda

---

### Post by daniell59 on 2012-02-05
My laptop would not boot off the flash drive. I took out the HD from the laptop. I  hooked it up to my desktop. I then installed Ubuntu from a flash drive into the HD of the laptop. Put the HD back into the laptop. I am presently using it.

---

### Post by varunendra on 2012-02-06
> **Old Pink said:**
> OK so Virtual PC won't recognize USB drives, but it looks like I'll be able to crack it with VMWare.
At the moment, no virtual machine can boot directly from a USB drive, no matter which platform you use - VBox, VMware,..... whatever.

An easy workaround is to boot the VM with [Plop]("http://www.plop.at/en/bootmanagerdl.html") iso (included in Plop Boot-Manager zip file). It will present you with a menu to further choose a boot device to boot from. Here you can choose USB at the bottom of the menu. All you need is a virtual machine which supports virtual USB port. I have personally tried it with Live USB flash drive on both VMware and VirtualBox. Of course, you don't have to install VM specific drivers (like VMware tools, Guest Additions, etc..) in this method (as they are simply drivers that run _on top of the installed guest OS_ to enhance its performance 'on the VM')

As for installation, I would suggest following:

[LIST]
[*]Live or alternate, choose a lightweight version which such an old hardware is capable of running. If 6GB is the size of HDD, I doubt it can even run Lubuntu (minimum 128MB RAM required). So you may wish to try an even [lighter distro]("http://www.tuxradar.com/content/whats-best-lightweight-linux-distro"), like Slitaz ([16-192MB RAM]("http://en.wikipedia.org/wiki/SliTaz#System_requirements")), DSL (16MB RAM), or maybe even Crunchbang (not sure about min. specs required, but is an Ubuntu derivative, and some of us like it even more than Ubuntu)
[*]For the installation method, just create a blank Virtual Machine (with no HDD) > Add your 6GB HDD to it > Boot the VM with the iso of desired OS > install it on the 6GB HDD.
[*]To test the installation, boot the HDD (via USB) using the Plop trick suggested above. Make sure to set the RAM same as your old laptop to get a close idea of the performance you'll get on it.
[/LIST]
Just for the record, I would request you to post your laptop specs and also which OS performance you found most satisfactory on it.

---

### Post by mastablasta on 2012-02-06
Chrunchbang is now based on Debian not anymore on Ubuntu. i think it takes arroun 4 GB on install depending what you install. 
 
perhaps Puppy linux (also has version based on Ubuntu repositories), bodhi linux etc...
 
RAM is the key and also CPU, but hard disk in htis case is also limited. So Slitaz might be worth considering.

---

### Post by Old Pink on 2012-02-06
I don't need to boot from USB on the live machine, I just need it to recognize the drive in the installation process. I'm booting from an .iso.

Everything works fine until chosing where to install the OS to, at which point only virtual HDs are listed. I can't find a way of giving a whole drive to the virtual machine.

Also, VMWare won't install. It gives some horribly vague error and just gives up the game.

---

### Post by varunendra on 2012-02-06
> **Old Pink said:**
> I don't need to boot from USB on the live machine, I just need it to recognize the drive in the installation process. I'm booting from an .iso.

Everything works fine until chosing where to install the OS to, at which point only virtual HDs are listed. I can't find a way of giving a whole drive to the virtual machine.

Also, VMWare won't install. It gives some horribly vague error and just gives up the game.
Since you mentioned VirtualPC, I thought you are trying this on windows, installing VMware (or any Virtualization software) on which is pretty easy.

However, The problem of accessing physical hard disks in VMs is exactly the same reason why using it as a USB one (using a usb enclosure) would have worked a treat! Although there IS a way to access entire physical hard disks (or partitions) from a VM, but they are a bit risky, especially on OSes like windows which love to mount all physical drives on startup.

If you don't have the option to attach the drive via a USB enclosure, check out the "Advanced Topics" in VirtualBox's help section. Adding a physical disk goes something like this (copied from VBox PDF manual):
> To create an image that represents an entire physical hard disk (which will not contain any actual data, as this will all be stored on the physical disk), on a Linux host, use the command
VBoxManage internal commands createrawvmdk -filename /path/to/file.vmdk -rawdisk/dev/sda

This creates the image /path/to/file.vmdk (must be absolute), and all data will be read and written from /dev/sda.
On a Windows host, instead of the above device speci&#64257;cation, use e.g. \\.\PhysicalDrive0.

---

### Post by Old Pink on 2012-02-06
I'm giving up on the Virtual PC side of things, far too complicated. All these software packages seem perfectly kitted to mount and have full use of an A: drive or D: drive, thought it'd be just as easy to give it an external hard drive.

No bother, I'll try the CD method now, just going to have to be extra careful with the GRUB thing.

---

### Post by lykwydchykyn on 2012-02-06
You could try the method I describe here:

[http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/](http://www.alandmoore.com/blog/2011/12/29/how-to-install-debian-offline/)

which uses debootstrap. It's a little technical, but not impossible if you follow step-by-step.

It works for debian or ubuntu, you just specify an ubuntu release name for the release instead of "stable" in step 2.2

---

### Post by Old Pink on 2012-02-06
It won't install, gets stuck at around 88%, half way through installing the kernel. Can only assume it's because it won't fit on the hard drive, I've had this exact issue with a 6GB hard drive before.

Best small distribution? Baring in mind it needs to be easy enough to install using this method?
[B]
Update:[/B] Gone for Xubuntu, some experience with this in the past.

---

### Post by Old Pink on 2012-02-06
> **Old Pink said:**
> It won't install, gets stuck at around 88%, half way through installing the kernel. Can only assume it's because it won't fit on the hard drive, I've had this exact issue with a 6GB hard drive before.

Best small distribution? Baring in mind it needs to be easy enough to install using this method?
[B]
Update:[/B] Gone for Xubuntu, some experience with this in the past.

Xubuntu gets stuck at the kernel installation too. Tried on two separate computers, with three different discs and two different operating systems. (2 Ubuntu discs, 1 Xubuntu disc) - only common denominator is the hard drive. This makes no sense at all?

---

### Post by Cheesemill on 2012-02-06
I'm pretty sure it's a disk space issue.

Once the installer has partitioned off some space for swap you're not left with enough for an install.

You could try using the Minimal Install CD and then adding a light WM such as Openbox, but even if you can install there won't be much room left for applications.

Take a look at this thread for some more options:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

It only gives values for RAM use but the ones with the smallest RAM use will probably be the ones with the smallest disk requirements as well.

---

### Post by Old Pink on 2012-02-06
> **Cheesemill said:**
> I'm pretty sure it's a disk space issue.

Once the installer has partitioned off some space for swap you're not left with enough for an install.

You could try using the Minimal Install CD and then adding a light WM such as Openbox, but even if you can install there won't be much room left for applications.

Take a look at this thread for some more options:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

It only gives values for RAM use but the ones with the smallest RAM use will probably be the ones with the smallest disk requirements as well.

5.6GB is enough for Xubuntu? 

Also I've tried ext3 filesystem instead of ext4, I figured maybe the old hard drive wasn't up to the new technology - no joy.

---

### Post by Old Pink on 2012-02-06
Reckon it's time to give up?

---

### Post by varunendra on 2012-02-06
> **Old Pink said:**
> 5.6GB is enough for Xubuntu? 

Also I've tried ext3 filesystem instead of ext4, I figured maybe the old hard drive wasn't up to the new technology - no joy.
Ext4 and ext3 are basically same, so it doesn't really matter which one you use.

You still haven't let us know your laptop's hardware specs. Are you sure it is capable enough to keep up with Xubuntu? (I have doubts even with Lubuntu!!).

How much RAM does it have, and what processor?
Have you tried formatting the drive then run fsck on it to check there are no bad-block issues?
Have you taken a look at SliTaz yet? (or at least Lubuntu)

In any case, it would be best to create partitions using gparted, then install the desired os on it. Do not let the installer create partitions, as most probably, it may create large swap partition depending upon the RAM in the current system.

Oh, and also, "6GB" in manufacturer's terms means 5.59GB in Operating system's view. And partitioning operation would further consume some space (although very tiny). So consider it no more than 5.5GB availability.

---

### Post by mastablasta on 2012-02-07
try bodhi linux. based on ubuntu (ubuntu is under it): [http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)
 
1.5Gb disk needed.
 
edit:
 
or you can go minmal install (about 1Gb needed):
 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
stick it in the other mashcine if it install well and then add more stuff to it (like desktop environment later on)

---

### Post by Old Pink on 2012-02-07
Its a Pentium 4 with 256MB RAM, I'll give you the full specs later. The computer can support it fine, I've ran full Ubuntu on less. The hardrive fried on it and I found this old 6GB one knocking about. 

I'll have a look at bodhi in a bit.

---

### Post by Old Pink on 2012-02-07
Also, remember I've not been running the installation on the laptop. I've been running it on this system, using the 6GB hard drive plugged in via. USB, and on another more powerful laptop, with the hard drive properly installed. Neither work. 

I could see your points about the specs being too low if it was failing on the laptop, but it's not. It's failing on two modern systems, with an old 6GB hard drive. The only common denominator causing the fail is the hard drive.

Like I said before, I've tried all combinations of two distributions (each with two CDs, four total), two computers, USB vs. hard install... the only thing that could be making this fail seems to be that hard drive. 

> **varunendra said:**
> You still haven't let us know your laptop's hardware specs. Are you sure it is capable enough to keep up with Xubuntu? (I have doubts even with Lubuntu!!).

---

### Post by Old Pink on 2012-02-07
Just for argument's sake, I'm going to create a 5.5GB virtual hard drive on this system, with 256MB RAM (less than I've currently been trying to install with), and try and run an installation using the Xubuntu CD I made (not the .iso, so I can test the burning process too)

Then I'll know for sure if it's the hard drive's size, the disk, or something else. Let's hope this fails too... (I think)

---

### Post by lykwydchykyn on 2012-02-07
If you suspect the drive is bad, have you tried running any diagnostics on it?  badblocks, fsck, or smartctl should tell you something.

---

### Post by varunendra on 2012-02-07
> **Old Pink said:**
> Also, remember I've not been running the installation on the laptop. I've been running it on this system, using the 6GB hard drive plugged in via. USB, and on another more powerful laptop, with the hard drive properly installed.
Yes, I'm completely aware of the fact that your current attempts are going on with a newer hardware. My concern was that is Xubuntu worth all those attempts you were making? Since I suspected that the original laptop for which you are installing it, might not be capable of handling it even if you succeed in the installation. But with a P4+256MB RAM, YES, it does seem much more reasonable now. But the HDD space is still a significant issue.

So, did you try fsck on the drive?


**_PS_:**
A few months ago, I was using Mint9 LXDE on an 8+ years old Compaq  laptop (presario 2100). I still have it, but is dead! I has a P4 (don't  remember the speed or model), and the RAM was upgraded to 256+512MB. But  the point is - I used it to run 3 Virtual Machines simultaneously (to  show it as a demo to my friends how they could practice networking  tricks on a single machine). The VMs were - Win Server 2003 (128MB RAM),  XP-Lite (128MB RAM) and DSL (64MB RAM). And for such an old laptop, its  performance was, with all three VMs running, Amazing .. to say the  least.

The point of this story is - LXDE is really light, and really great! You  should try it, regardless of what you prefer in the last.

---

### Post by Old Pink on 2012-02-07
> **lykwydchykyn said:**
> If you suspect the drive is bad, have you tried running any diagnostics on it?  badblocks, fsck, or smartctl should tell you something.

> **varunendra said:**
> But the HDD space is still a significant issue.

So, did you try fsck on the drive?

I've ran Windows Diagnostics on it, I'll boot a Ubuntu Live CD and run fsck on it now. 

> **varunendra said:**
> **_PS_:**
A few months ago, I was using Mint9 LXDE on an 8+ years old Compaq  laptop (presario 2100). I still have it, but is dead! I has a P4 (don't  remember the speed or model), and the RAM was upgraded to 256+512MB. But  the point is - I used it to run 3 Virtual Machines simultaneously (to  show it as a demo to my friends how they could practice networking  tricks on a single machine). The VMs were - Win Server 2003 (128MB RAM),  XP-Lite (128MB RAM) and DSL (64MB RAM). And for such an old laptop, its  performance was, with all three VMs running, Amazing .. to say the  least.

The point of this story is - LXDE is really light, and really great! You  should try it, regardless of what you prefer in the last.

That is pretty impressive, I'll certainly have a look. Currently I'm playing around with Slitaz, I really just want something with a decent looking interface that can call up a good web browser. 

Ubuntu/Xubuntu was my priority as I've got a lot of past experience with them, and I figured if it turned out the laptop was quick enough to use for other stuff, I'd have no problem with that in Ubuntu.

---

### Post by Old Pink on 2012-02-07
Managed to install Slitaz using a host laptop. Install went smoothly. 

Inserted hard drive into desired laptop, GRUB boots fine, selected Slitaz and I'm stuck at 

> 
root hd(0,0)
 Filesystem time is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.30.6-slitaz root=/dev/hda1
   [Linux-bzImage, setup=0x3000, size=0x21a850]


**Update:** Same issue in the host laptop. Trying re-install.

---

### Post by Old Pink on 2012-02-07
Right, going to try DSL, if that doesn't work, **** it - I give up.

---

### Post by Old Pink on 2012-02-07
Update: DSL installed and running fine. Hard drive FSCK'd and passed.

DSL is excruciating in terms of drivers (wireless, video, everything...) - really want to get Ubuntu or at the very least Xubuntu up and running. Given I've proven all my hardware is fine and DSL is now running, does anybody have **any** ideas?

---

### Post by varunendra on 2012-02-08
> **Old Pink said:**
> Update: DSL installed and running fine. Hard drive FSCK'd and passed.
Haa.. at last..!

> **Old Pink said:**
> Given I've proven all my hardware is fine and DSL is now running, does anybody have **any** ideas?
[Lubuntu 10.04 minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#A10.04_32_Bit") (supported untill April 2013) or [Mint9 LXDE]("http://www.linuxmint.com/edition.php?id=60") (supported untill April 2013, same as the latest version)
(sorry if it sounds as "imposing", maybe my brain has got biased due to  repeating the word "LXDE" so many times for last couple of days ;))

**_System Requirements_:**

**Lubuntu 10.04 minimal** (quoted from: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04):]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04%29:")

[LIST]
[*]32 bit minimal install - For those people with less than 160MB of  available RAM (Typically 192MB for computers with built in graphics). It  is a full installation but does not use the standard installer. This  minimal version is discussed at [10.04 Minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
[*]Less than 4.3GB hard disk space (quoted from "11.10 > Alternate" section of the same above page)
[/LIST]


**[Mint 9 (LXDE)]("http://blog.linuxmint.com/?p=1473"):** 

[LIST]
[*]x86 processor
[*]192 MB of system memory (RAM)
[*]3 GB of disk space for installation
[*]Graphics card capable of 800×600 resolution
[*]CD-ROM drive or USB port
[/LIST]
I have a few other options in mind as well, but they don't seem practical for you.



**_EDIT_:**
As for Xubuntu, I hope you have already noticed this (quoted from: [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) > Min. Sys. Req.):
> **Memory** You need 256 MB RAM to run the Live CD or 256 MB  RAM to install. The Alternate Install CD only requires you to have 64 MB  RAM at install time.
 *Once installed, *Xubuntu can run with starting from 256 (or even just 192) MB RAM, **but it is strongly recommended to have at least 512 MB RAM**.

**Hard disk space**
 To install Xubuntu with the standard installer  (Ubiquity), you need 4.4 GB of free space on your hard disk. The  Alternate Install CD only requires you to have 2 GB of free space on  your hard disk.


---

### Post by lykwydchykyn on 2012-02-08
> **Old Pink said:**
> Update: DSL installed and running fine. Hard drive FSCK'd and passed.

DSL is excruciating in terms of drivers (wireless, video, everything...) - really want to get Ubuntu or at the very least Xubuntu up and running. Given I've proven all my hardware is fine and DSL is now running, does anybody have **any** ideas?

Did you try the method I suggested with debootstrap?

---

### Post by Old Pink on 2012-02-08
> **lykwydchykyn said:**
> Did you try the method I suggested with debootstrap?If I'm not mistaken, I need a functional Linux system and a fresh hard drive for this method? I couldn't do it from XP? 

I don't have a computer running Linux currently.

---

### Post by Old Pink on 2012-02-08
> **varunendra said:**
> Haa.. at last..!


[Lubuntu 10.04 minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#A10.04_32_Bit") (supported untill April 2013) or [Mint9 LXDE]("http://www.linuxmint.com/edition.php?id=60") (supported untill April 2013, same as the latest version)
(sorry if it sounds as "imposing", maybe my brain has got biased due to  repeating the word "LXDE" so many times for last couple of days ;))

**_System Requirements_:**

**Lubuntu 10.04 minimal** (quoted from: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04):]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04%29:")

[LIST]
[*]32 bit minimal install - For those people with less than 160MB of  available RAM (Typically 192MB for computers with built in graphics). It  is a full installation but does not use the standard installer. This  minimal version is discussed at [10.04 Minimal]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
[*]Less than 4.3GB hard disk space (quoted from "11.10 > Alternate" section of the same above page)
[/LIST]


**[Mint 9 (LXDE)]("http://blog.linuxmint.com/?p=1473"):** 

[LIST]
[*]x86 processor
[*]192 MB of system memory (RAM)
[*]3 GB of disk space for installation
[*]Graphics card capable of 800×600 resolution
[*]CD-ROM drive or USB port
[/LIST]
I have a few other options in mind as well, but they don't seem practical for you.



**_EDIT_:**
As for Xubuntu, I hope you have already noticed this (quoted from: [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) > Min. Sys. Req.):
RAM doesn't concern me at all. I'm happy for the system to be slow, I just want it up and running. It's easier to strip down than it is to build up. 

Is it possible for a hard drive to pass fsck and still be faulty? Xubuntu and Ubuntu both get to around 60-80% through the base installation then fail. Maybe DSL only worked because it was too small to reach damaged sectors further on in the disk? 

I've tried different filesystems, formatting the partition using GParted before the installation (and not re-formatting using the installer) - everything. It makes no sense. 

I'm happy to try Lubuntu or Mint 9, but are they going to have the drivers I need installed? It's pretty tough fannying around getting drivers to work on distributions like DSL, when they don't even have "make". 

Also, I'm currently out of blank discs... went through nine over the past two days trying different burns and distributions. :lol:

---

### Post by Old Pink on 2012-02-08
Also is it unusual that when my installation fails, around 60-80% through the base installation, when I boot into Slitaz and mount the hard drive, there are no files on it? And there's only 256MB (give or take) taken up? 

I think it's a lost cause. Dodgy hard drive that somehow sails through Fsck.

---

### Post by Old Pink on 2012-02-08
Last resort. I'm plugging the hard drive into this computer via. USB, and booting the 7.04 Live CD, and trying to install from there.

I'm pretty sure I've had 7.04 on this hard drive before, maybe it's just newer Ubuntu giving me grief.

---

### Post by varunendra on 2012-02-08
> **Old Pink said:**
> Also, I'm currently out of blank discs... went through nine over the past two days trying different burns and distributions. :lol:Hmm.. that's where re-writable discs are handy (but only with a healthy optical drive). ;)

> **Old Pink said:**
> when I boot into Slitaz and mount the hard drive, there are no files on it? And there's only 256MB (give or take) taken up?
Now that's some info. My first guess is a bad PBR area (partition boot sector) that contains file allocation table. What is happening might be this-

Installer detects the partition and available space fine > starts copying files to it > then after 60-80% comes the stage to configure the copied files, only to find that the files are missing!!

Try manually creating or copying files on the partition > reboot and see if the files are still there. If they are, then maybe it goes wrong when it attempts to write to the PBR.

Well.. these are just some guesses about causes, can't think of solutions right now :(

---

### Post by Old Pink on 2012-02-08
USB connected hard drive isn't showing up in the LiveCD... Hard drive shows up fine when hard-installed in a laptop, plugged in via USB when XP is running and plugged in via. USB when alternate CD is running, but it's nowhere to be seen in LiveCD. Tried reformatting it, everything, whether it's NTFS, Fat32, ext3 or just plain unformatted, it won't show up.

Yet I plug a USB stick in, and that pops up instantly?

---

### Post by Old Pink on 2012-02-08
I can hear the CD whir and think about it when I plug the HD in... How do I do that thing in terminal where I see the log? (Recent devices etc)

---

### Post by Old Pink on 2012-02-08
Found it, its constantly saying "New high speed usb device using ehci_hcd and address **" - looks like its trying time and time again to process it.

---

### Post by Old Pink on 2012-02-08
I've concluded that the hard drive is faulty after running more tests. 

I'm gutted, really wanted to give Ubuntu another shot. Don't much fancy partitioning this again though... 

Shame. Thanks for your help anyway, everyone.

---

### Post by varunendra on 2012-02-09
Sorry to see you give up. Seems pretty reasonable though, with so many different attempts only to see them fail..
Anyway, answer to one of your questions I missed earlier:
> **Old Pink said:**
> I'm happy to try Lubuntu or Mint 9, but are they going to have the drivers I need installed?They share same kernel and 'almost' same repositories as Ubuntu. So yes, you can be pretty sure about drivers, applications and other capabilities.

And the (approx.) 256MB space you see as 'taken up' is actually the space 'reserved' for root in linux filesystems. It is exactly 5% of the total space on each partition, and you can change this %age with *tune2fs* command (can even set it to 0%, although not recommended).

As another wild shot, you could try clonezilla to 'restore' an image of a preinstalled disk (of a VM) over to the physical one while it is connected via USB. Although I have already suggested something similar in [post #12]("http://ubuntuforums.org/showthread.php?p=11668110&postcount=12"), this would be different since you would be restoring image from a real (not virtual) machine which is able to detect the drive via USB. It is important because VMs may not be able to use usb unless virtual drivers are installed on the running guest OS (which would be clonezilla live in this case). So the approach would be like (assuming you'd be using VirtualBox on Ubuntu):

[LIST=1]
[*]install mint lxde on a VM (with a 5 or 5.5 GB virtual HDD)
[*]After the installation is finished, add another virtual HDD to it (to save the cloned image on it), and format it.
[*]boot the VM with clonezilla live iso
[*]create a 'full-disk' image of the OS hdd, saving it on the other hdd
[*]reboot into installed mint > install "Guest Additions" on it (so you can enable copy-paste between guest and host machines)
[*]copy the image over to the actual hdd
[*]reboot the (physical) computer with clonezilla live CD (yup! yet another cd ;))
[*]attach the 6GB HDD via USB
[*]'Restore' the image onto the 6GB hdd.
[*]Reconnect the drive to the laptop and boot .. and celebrate your new LinuxMint!! (well.. hoping or dreaming doesn't cost anything, right?)
[/LIST]
The only catch I can think of in this process would be - what if clonezilla live refused to detect the drive via usb?
But fortunately, there is an easy answer - use dd command instead to restore the image - from the OS which is able to detect it.


Also, steps 5 onwards can be completely omitted if you can successfully connect the drive to the VM (instead of a virtual hdd in step 2), as I suggested in post #12. In my experience, connecting USB drives to VBox (or VMware) VMs is trivial once guest additions are installed. And I think copying a preinstalled image rather than a direct installation has better chances of survival on that disk (i.e., overcoming the 'empty partition' problem in post #35).


I can't guarantee it'll go smooth, but is definitely a 'slightly different' approach, which I have successfully tried a few times due to different reasons.


Hope you'll try that whenever you think you have time to give it yet another shot.


Good Luck!

---

