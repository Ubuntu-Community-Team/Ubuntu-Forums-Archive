---
title: "Installing Ubuntu on an external HD"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by senor.ehlert on 2008-10-08
Hello, this is my first post and I have absolutely no experience with ubuntu or any other form of linux. I have only used PC and a little mac, but I am finding myself wanting to find something new. So i downloaded ubuntu burned the ISO and tried it by running it off the disc without installing it. I have to say I like it, but I do have some questions.

Although I am fed up with windows I do not want to get rid of it entirely (at least not yet), so I would like to do a dual boot. I would prefer to do the dual boot on an external HD. Is this even possible? I haven't seen anything written about it anywhere. I would maybe in the future like to do a dual boot on my interal laptop HD. However, my computer is running Windows Vista Ultimate 64-bit and I have seen some bad incidents with partitions messing up the recovery partition. Is this true? Can I dual boot my internal HD without screwing up or removing the factory recovery partition?

Although I would welcome any info on partitioning and dual booting my internal HD I would prefer to start with my external HD. Thanks for the help.

---

### Post by rybaxs on 2008-10-08
Yes. it is possible, try to run the Ubuntu Live if the external HD is available.

---

### Post by senor.ehlert on 2008-10-08
Ok. Thanks. How would I do that? Just partition the HD and install ubuntu?

---

### Post by rybaxs on 2008-10-08
Wait the minute? 

> 
Just partition the HD and install ubuntu?


You mean the internal or the external?,
Try to run the Ubuntu Live CD, just follow the wizard, you will be bump on the partition section of the wizard.. Just click the desired disk you want to partition or select the disk you want to install your Ubuntu

Do not worry about Ubuntu, it will not change entirely your system..

What do you want? Dual boot? previous OS and Ubuntu? or single OS on different disk?

---

### Post by mlentink on 2008-10-08
Entirely possible.

Boot up with the LiveCD and make sure the USB-drive is connected. Make sure to install Ubuntu on the external disk (most likely called sdb rather than sda) After the partioting phase be sure to select the "advanced" option to be able to install GRUB (the boot loader) on the external drive (i.e. on sdb rather than the primary hard drive). Let the installation process complete. Do not reboot yet, or reboot with the LiveCD. Edit the \boot\grub\menu.lst on the USB-drive, and change all references to sdb to sda. If there are any references to your windows installation on the primary harddisk, you will need to change those to sdb in place of sda.

Now when you reboot make sure to select the USB-drive. Your BIOS should allow you to do so just as you were able to select the CD-ROM drive to boot the LiveCD.  Ubuntu will boot up without any interference with your existing harddisk.

Hope this helps.

Welcome to the free world!

---

### Post by vanadium on 2008-10-08
I do not recommend installing Ubuntu on the external CD. Especially as a beginner, you will run into issues following not standard approaches and then you might find "Ubuntu a bad OS".

If you want to experience Ubuntu but do not wish to touch your existing system, then a recommand a Wubi install. With a Wubi install, you start the installation of Ubuntu from within Windows, using a Windows installer. Ubuntu is installed in a virtual file system, that resides in a regular file on your Windows disk.

The result is a true dual boot system. The only difference is that Linux will run from a virtual file system instead of from a dedicated partition. This obviously is less ideal in terms of performance and reliability than having its own dedicated partition. The performance hit is rather theoretical: you are not really going to feel that.

Tired from Ubuntu? Use Windows "uninstall" to remove the installation and reclaim the disk space.

Just my advice.

---

### Post by mlentink on 2008-10-08
Much as I agree with vanadium's approach, that was not as I understood the OP's question. Even though the approach I suggested is relatively risk-free (I use it quite frequently to test out new alpha versions or other distros), for a true 'Absolute Beginner' the Wubi approach is probably the most intuitive and painless. 
To the OP: Wubi will do nothing to your existing partitions, including your recovery partition.

---

### Post by vanadium on 2008-10-08
mlentink: you are perfectly right that the question was different. I think however that it is unwise to try to guide a beginning linux user over non standard procedures, so I made other recommendations. I would not have answered this were this not the Absolute Beginners forum with a user stating explicitly he has no linux/unix epxperience whatsoever.

---

### Post by Radioman991 on 2008-10-08
To the OP, yes it is possible, and in my situation, it works EXTREMELY well.

I have a company laptop, which has an encrypted internal HDD with Winders on it.  Here's what I did.

1) Went to BIOS, set USB to first boot device
2)  Physically removed the Company internal HDD, (I had killed the first one...oops)
3)  Plugged in the LACIE 100 gig external USB drive, which had no OS, so non bootable, and booted the laptop with the 8.04 Live CD
4)  Proceeded to install 8.04 to the 100 gig Lacie...which was the only hard drive detected.
5)  Enjoy.

When I need company apps, I can boot Windoers...just remove the Lacie from the USB port.  When I want to run Ubuntu...which is just about anytime I am off the clock...I shut down the machine, plug in the Lacie, and power on.  Can't even tell it is not an internal drive...although I am sure there ARE some speed issues, it's difficult to tell.

Hope this helps.

PK

---

### Post by hotrod6657 on 2008-10-08
> **Radioman991 said:**
> To the OP, yes it is possible, and in my situation, it works EXTREMELY well.

I have a company laptop, which has an encrypted internal HDD with Winders on it.  Here's what I did.

1) Went to BIOS, set USB to first boot device
2)  Physically removed the Company internal HDD, (I had killed the first one...oops)
3)  Plugged in the LACIE 100 gig external USB drive, which had no OS, so non bootable, and booted the laptop with the 8.04 Live CD
4)  Proceeded to install 8.04 to the 100 gig Lacie...which was the only hard drive detected.
5)  Enjoy.

When I need company apps, I can boot Windoers...just remove the Lacie from the USB port.  When I want to run Ubuntu...which is just about anytime I am off the clock...I shut down the machine, plug in the Lacie, and power on.  Can't even tell it is not an internal drive...although I am sure there ARE some speed issues, it's difficult to tell.

Hope this helps.

PK

That's almost the same way i did my fist trial of Linux.  The issue with not removing the other harddrive for the install for me was always that Linux always messed up the Master boot record in windows when i installed it on the external drive.  It's only a problem if you remove your linux partition.  In the end you just have to use a windows CD to fix the MBR.

Regardless, I would say that disconnecting your internal hard drive, plugging in the external hard drive, setting the bios to boot the external hard drive first, and then booting up the live CD with just the external HD attached and installing it there is your best option, and the most risk free.

When the install is done reattach your internal HD and you're good to go, just turn off the External Drive when you want to get back to Windows.

The only disclaimer i would mention is if you ever have lag or feel like speed is an issue remember you're running through an external drive and usb.  That's really the only place you could possibly see issues and i doubt they would be major.

Good Luck and enjoy!

hotrod

---

### Post by Keen101 on 2008-10-08
I am running Ubuntu from external USB HDD right now! It works great.

This is what i did:

1. get Live-CD
2.Unplug internal HDD (just to be safe, and so i don't have grub problems)
3.Install Ubuntu to external HDD (should be the only one)
4.restart, and configure BIOS to boot from USB before internal HDD.
5.When i need Ubuntu i plug in USB HDD and power on...goes straight to Linux.
6.IF i need windows i just unplug usb hdd and power on. Goes right to Win.

hope that helps. Hope you get it working. It should work fine. Plus it's portable. (i use mine at school too)

---

### Post by Radioman991 on 2008-10-08
> **hotrod6657 said:**
> That's almost the same way i did my fist trial of Linux.  The issue with not removing the other harddrive for the install for me was always that Linux always messed up the Master boot record in windows when i installed it on the external drive.  It's only a problem if you remove your linux partition.  In the end you just have to use a windows CD to fix the MBR.

Regardless, I would say that disconnecting your internal hard drive, plugging in the external hard drive, setting the bios to boot the external hard drive first, and then booting up the live CD with just the external HD attached and installing it there is your best option, and the most risk free.

When the install is done reattach your internal HD and you're good to go, just turn off the External Drive when you want to get back to Windows.

The only disclaimer i would mention is if you ever have lag or feel like speed is an issue remember you're running through an external drive and usb.  That's really the only place you could possibly see issues and i doubt they would be major.

Good Luck and enjoy!

hotrod


I couldn't repair my MBR as I didn't have to corporate Windows disk, nor the admin password.  I had to "VERY MEEKLY" crawl to Helpdesk for another drive  :-)  I am a telecommuter, and am 200+ miles from the closest office :-)  Thats why I did the physical removal, and don;t use Grub in that situation.

On my home machine, which has 2 internal IDE drives, I have Windows on 1 drive, and Ubuntu on another, and use Grub to select the OS

I have noticed no real speed issues that are show stoppers.  Machine is a Thinkpad T43p, with 2 gig RAM.  I even run a Windows VM on the external drive.  now THAT tends to boot a little slow, but it works.

---

### Post by SunnyRabbiera on 2008-10-08
Its possible to do this as long as you have over a gig of space.
If you have say a 40 gig external then you can have enough room to play around with linux while at the same time have some storage room.
At max Ubuntu needs at least 4 gigs to start off with, the kernel itself takes about 3 gigs on its own and there is swap memory too.
But if you have like a 10 GB external its still worth a shot, anything under 6 gigs is a waste of time.

---

### Post by vanadium on 2008-10-08
Nice and simple approach, except that you need to disconnect the hard drive. No problem for a desktop, but I would not dare to open a laptop, though. However, if you are very, very careful, it is probably possible to direct the Ubuntu installation program where to install the bootloader as not to touch the boot sectors of your internal drive. Thus you probably could do this without hardware manipulations.

---

### Post by Radioman991 on 2008-10-08
> **vanadium said:**
> Nice and simple approach, except that you need to disconnect the hard drive. No problem for a desktop, but I would not dare to open a laptop, though. However, if you are very, very careful, it is probably possible to direct the Ubuntu installation program where to install the bootloader as not to touch the boot sectors of your internal drive. Thus you probably could do this without hardware manipulations.

The T43p has a single screw, and you can pop the HDD out without opening the entire lappy.  YMMV

---

### Post by hotrod6657 on 2008-10-08
ThinkPads in general are very good about allowing the user to do this sort of stuff.  My laptop was a T60p.  No voiding of the warranty, just a simple single screw to pop out the drive.  I had tried directing the install to put GRUB somewhere else with no luck, it always messed it self up.

I can't recall if the OP said if it was a desktop or laptop...

---

### Post by senor.ehlert on 2008-10-08
Thank you all for the feed back!

I have a laptop, so I don't really want to screw around with opening it and disconnecting the internal HD. So the Wubi install sounds pretty good to me. How would I go about doing this and where can I find Wubi? And it shouldn't matter that I am running 64-bit Vista?

Thanks again for all the help.

---

### Post by hotrod6657 on 2008-10-09
The WUBI install should be with your live CD.  I think you can just insert the  CD when your computer is booted into Windows and it should have an option to install within windows or something like that.  Never tried it myself but I believe it's that simple.

it shouldn't matter that you're running 64bit vista.  You can install either the 64 or 32 bit versions of Ubuntu, just depends on what CD you have.

---

### Post by razy60 on 2008-11-05
I have been wanting to do this only thing is that my laptop is still under warranty so dont want to open it up.

i have an a old pc that i use for internet and email, if i disconnect the drive in that and connect the external to it then do an install onto the external drive, would i be able to use it on my laptop or even on a another pc,(connecting it using the usb port)

Basically a fully functioning OS on an external drive that i can use any where. + as the drive that i have is 320gig in size would it be possible to partition it so that say 160 is used for Ubuntu (fat32) and 160 in ntfs for general storage and use by whichever or another combination.

thanks for any help 
Raz

---

