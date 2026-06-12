---
title: "can't boot anything, help!"
date: 2015-06-13
forum: New to Ubuntu
---

### Post by Clark_Turner on 2015-06-13
I have a Dell Inspiron E1405 that I tried to load Ubuntu 14.04 LTS onto with a live CD and I chose the option to wipe out Windoze and just install LInux.  The installation crashed at some point and was dead in the water.  Now I can't boot the live CD, the iso on a USB drive or (of course) from the HD.  I've loaded Boot Repair to get a terminal and boot repair tool, run the repair to the MBS and nothing changed.  I still can't boot the live CD (DVD) - I've set the boot priority to the CD/DVD drive and manually chosen it (via F12 during boot) and still nothing.  The only thing I can get to boot is boot-repair. Boot repair tells me to report this URL for my boot info:
[http://paste.ubuntu.com/11711622](http://paste.ubuntu.com/11711622)

Any tips?  

Clark

Just tried to boot from the live CD and got a "No bootable devices" error.  The onboard diagnostics seem to show that it passes all tests.
I'll boot back up to the boot-repair tool.

---

### Post by sandyd on 2015-06-13
It's odd that you can't boot the livecd after the installation crashed. It is possible that the livecd was corrupted during burning or during the download process.

At the moment, from the output of boot-repair, it seems that
a) The boot partition for Ubuntu has been created
b) The swap partition has been created inside the extended partition
c) The root partition and/or additional partitions are missing

You will need to do a reinstall with either a liveUSB or a liveDVD by downloading it on another computer and setting it up there.

Side note: You will need to use a utility to copy the ISO to the USB drive such as [unetbootin ]("http://unetbootin.sourceforge.net/")or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") in order to make the USB drive bootable

---

### Post by RobGoss on 2015-06-14
Hello and welcome, I'm note sure what the specs are for your machine but the version you installed might not work well with your computer. You have a few choices ether make a new CD or USB, and see if it installs correctly or you can try a lighter distribution like Lubuntu...

---

### Post by grahammechanical on 2015-06-14
I do not understand how you could run Boot Repair from a live session if you cannot run the Ubuntu live session/install session from either a CD/DVD or a USB memory stick.

Anyway, Boot Repair cannot do any repairs because Ubuntu is not installed. Two things need to happen to the boot loader (Grub). 1) Grub needs to be installed into the MBR (Master Boot Record) of the hard disk. 2) The Grub configuration files need to be placed in the /boot/grub/ directory in the partition Ubuntu is installed in. But Ubuntu is not installed and there is no /boot/grub/ directory.

Regards.

---

### Post by Steve_Horan on 2015-06-14
Going to have to use another computer and grab a new ubuntu live cd. When your machine boots, are you prompted with grub? If so you can rebuild grub with the grub2 command line assuming that the directory structure is there and the linuz and initrd images were installed. It sound's like this is not the case however.

---

### Post by Clark_Turner on 2015-06-14
Wow, thanks for all the prompt replies.  This forum is great.  Further information: 

 I did have the liveCD working and running live linux on this machine when I first attempted the install of Linux.  That crashed and ever since, I can't boot from the liveCD.

I did go to another machine and downloaded the linux ISO to a DVD (at a slow speed) and this second one didn't work either.

I did use unetbootin to put the ISO on an SD card using a different machine.  I set the boot priority to the USB and this didn't work either.  

So, at present, I can only boot up to the boot repair DVD I burned (seems to be live lubuntu) and I have rudimentary functionality (a terminal, a browser, some basic tools.) 

I can't see the DVD drive filesystem (directory structure shows the HD but I find I cannot download Ubuntu to it using the browser).

I'm a complete novice at all this, but I am able to install grub using apt-get in the terminal.  Is grub or grub2 useful if I install it?

Clark

---

### Post by dino99 on 2015-06-14
I've no experience with the Dell pc, hope it has not a Dell's 'hidden' partition, like some brand do. If such a case, then start to do a low format with the [http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/), or try first to reformat with gparted live ; then try reinstalling

---

### Post by Steve_Horan on 2015-06-14
Clark,

It sounds like you possible my have attempted to accidentally install ubuntu on the USB you had the live installation on. It would be best to recreate the ubuntu installation usb drive (sorry I was not clear at first) and attempt to reinstall again. I do not believe the rescue disk will be of any use atm. Recreate the live installation disk and attempt the installation again and be careful of the hard drive you are installing this on. Let us know of any issues during that process.

---

### Post by Clark_Turner on 2015-06-14
Steve -  I have wiped my SD card clean and used unetbootin to put the ISO on it.  I see that the SD card does now have some files on it, one is binary.  One possible issue with unetbootin was that it gave me the message that it couldn't find p7zip, but it proceeded just fine and did produce the files on the SD boot card.  I tried to boot from the card and still it won't work.  

I have made several different DVD's of the ubuntu ISO, the last was burned to the DVD at low speed  (6x).  It still won't boot up.  Can I use it and boot ubuntu live on a machine where I already run ubuntu?  If I could test it I would, but don't know whether the live session would boot up with ubuntu already underneath the hood.  I just want to make sure its not a bunch of defective DVD's (although the boot repair disk is written to one of the same batch of DVD's and it is working on the target machine.

I have not tried a low level format on the HD, not sure what that would do for the problematic boot sectors.  There is a version of grub that comes with the boot repair disk (lubuntu) and I see it referenced a lot when working with these problems, just not sure if it would help me in this case.

Thanks guys, it is really a wonderful service you all provide.  I'll join you if/when I get through this problem (at least if someone has a similar problem.)

Clark

---

### Post by cariboo on 2015-06-14
You realy aren't telling us what happens when you try to boot from the live cd/usb. Do you see anything on screen when trying to boot?

---

### Post by Clark_Turner on 2015-06-15
First I set up the boot priority to go to the DVD drive as priority 1.  I put the live DVD in and and restart the computer.  It goes through the bios stuff and I've often hit the F12 (one time boot priority menu) to make sure it goes to the DVD drive (I've tried this several ways with boot priority, they all come to the same end).  After the DELL bios stuff ends, the DVD drive spins up for a little while then spins down.  The next message I see (with an annoying beep) is "[No bootable devices, strike f1 to retry boot, f2 for setup utility, press f5 to run]("http://en.community.dell.com/support-forums/disk-drives/f/3534/t/19250087") diagnostics"    It also does this when I try to boot from a USB drive (SD card).  

Clark

The mystery to me is why does the computer run OK from the live DVD with boor repair disk (that I burned) and then with the live linux DVD the computer doesn't recognize the drive at all.

---

