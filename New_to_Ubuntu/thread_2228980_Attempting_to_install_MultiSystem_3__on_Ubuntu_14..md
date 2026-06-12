---
title: "Attempting to install MultiSystem 3  on Ubuntu 14.04..."
date: 2014-06-10
forum: New to Ubuntu
---

### Post by Mike_Walsh on 2014-06-10
Evening all.

I've only been on Linux for a few weeks, so I'm coming up against obstacles that I guess more experienced users will think, "Well, ANYBODY should know that..."

I'm trying to install Multisystem 3 on a 32Gb thumbdrive, so I can add some more Linux distros to it. It downloads as "install-depot-multiboot.sh.tar.bz2", and extracts quite happily to the desktop, as specified in the installation instructions. I'm following the instructions on 'http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/', which is where I got the USB setup instructions that eventually led to 'Trusty Tahr' being installed on here...a process which was totally trouble-free, so I'm happy to trust the site.

The trouble starts when I try to run it. I'm supposed to double-click the icon, and choose from "Run in terminal", or "display contents". However, when I double-click the icon, I get a message come up, telling me "Cannot open install-depot-multiboot.sh.; Archive type not supported".

So, my question is, quite simply, how do I enable support for this type of archive file? What do I need to install, or do I need to update from one of the repositories? How would I go about it?

Mike .

---

### Post by monkeybrain20122 on 2014-06-10
Is this what you are trying to do? [http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

I have been using it to make multiboot usbs for a while, but multisystem itself is not installed in a usb, it is installed in Ubuntu itself. 

The link you used is outdated, for that you need to extract the tar file, in which there is an install script, make the install script executable and then run it in the terminal. It will then install multisystem and add a repository to your sources so it will be updated through the normal update mechanism. 

But instead of doing that check out the link above for updated installation instructions.

---

### Post by oldfred on 2014-06-10
It is not all that difficult to manually install grub and use grub to boot ISO.

But with a 32GB flash drive I would (as I have with my 32GB flash drive) create a / (root) partition and install a full Ubuntu or Lubuntu if system is lower on resources. And then add extra ISO as you desire.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Flash drive is similar to hard drive if a full install:
      
 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by Mike_Walsh on 2014-06-10
Hi, guys.

Well, thanks for the replies. Monkeybrain, I'll have a look at the link you've provided, and give that a try.

Oldfred, thanks for the info. I'll have a look at that, too, especially the section on booting from a second hard drive; I have a Seagate 500 Gb external USB3 drive which has already been set up with several partitions, so I'll see if I can do it that way

I'm attempting to set up a dual-boot system with Ubuntu and Zorin's OS Ultimate 64bit, so; I don't really mind which way works, as long as I can get the Live session to boot, so that I can then install the Zorin alongside the Ubuntu. If I have to use Gparted to reformat and/or alter the partitions, then I do; I've already got info on how to do that.

Thanks, guys. Will let u know how I get on. Cheers!

Mike.

---

### Post by oldfred on 2014-06-10
I have totally converted to booting ISO directly from another partition on one of my old hard drives. Using that I do not have any issues of mounted interfering with install type issues.

I still copy ISO to a flash drive for booting, but that is for emergency boot or I have several repair ISO on several flash drives. 

I have not tried booting Zorin, so I do not know if it needs special boot parameters or not. Each ISO seems to need different settings and that is one advantage of the ISO boot install scripts as they have resolved those issues for most ISO that can be booted via ISO. But sometimes a newer release changes things and then it does not work.

---

