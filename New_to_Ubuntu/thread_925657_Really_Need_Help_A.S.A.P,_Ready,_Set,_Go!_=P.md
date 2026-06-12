---
title: "Really Need Help A.S.A.P, Ready, Set, Go! =P"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Solais on 2008-09-20
Ok, I have been here for a while and I know I can trust you guys:). Ok Im running on Hardy Heron right now, full. I want to format my hdd and install xp, then a partition for Linux. Ok, I suck on pc stuff but I want to study pc in college and I want to learn about pc alot and such. Ok I new to know step by step how to do this, my hdd is SATA and I don't have a floppy drive, I don't know what my Mother Board manufacturer is so I can't download the driver thing anyway, they told me I need nlite but when I got nlite it did not work anyway and it told me that i needed Network Net from windows to work and i couldnt install it, but first I guess I need my mother board info and such, so anyone up to help me on this :)?

---

### Post by starcannon on 2008-09-20
You could actually just use gparted to resize your partitions, allowing you space for the xp install, no need to scrub it entirely.

Dualboot may not even be what you need; if your not playing graphic intensive windows games, then perhaps a better choice would be installing Windows XP to a Virtual Machine like Sun's Virtual Box perhaps? Its certainly worth a look see, and takes a lot of work out of the equation if it will meet your needs.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

GL and have fun.

---

### Post by mc4100 on 2008-09-20
> **starcannon said:**
> You could actually just use gparted to resize your partitions, allowing you space for the xp install, no need to scrub it entirely.

Dualboot may not even be what you need; if your not playing graphic intensive windows games, then perhaps a better choice would be installing Windows XP to a Virtual Machine like Sun's Virtual Box perhaps? Its certainly worth a look see, and takes a lot of work out of the equation if it will meet your needs.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

GL and have fun.

Keep in mind that if you re-size, then install XP, you will also have to reinstall the GRUB bootloader, as it will be wiped during the Windows installation.

---

### Post by Solais on 2008-09-20
> **mc4100 said:**
> Keep in mind that if you re-size, then install XP, you will also have to reinstall the GRUB bootloader, as it will be wiped during the Windows installation.

I wish to wipe everything, have everything important in a portable hard drive i want to make this pc new, nothing linux related for now ;), its my dads and brothers pc, he plays wow at high detail and a few games that need alot of xp stuff, i just want xp as main and after a while make a partition for linux for me to f around :)

---

### Post by kansasnoob on 2008-09-20
I was also thinking VirtualBox:

[http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02](http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02)

---

### Post by Solais on 2008-09-20
Is this enough info to know where to go for the stuff i need for the boot cd?
  *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32 module=pata_via

---

### Post by kansasnoob on 2008-09-20
Well, you may be able to fiddle with the BIOS to make the SATA drive "look like" an IDE drive. But google for posts relating to downgrading from Vista to XP. Like this:

[http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=243153&messageID=2665617](http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=243153&messageID=2665617)

That's kind of a common thing.

---

### Post by cariboo on 2008-09-20
If you want to start from scratch, boot from your windows installation disk When you get to the partitioning step just clear all the partitions then set up your windows partition. What I usually do if I'm setting up a computer to dual boot is to use half of the hard drive for Windows and the other half fo whatever Linux distribution I plan on installing. I just partiton and format the windows half of the hard drive and leave the linux half blank. Then when I'm ready to install linux I use the distribution's partitioner to partition the linux half.

You are going to need the make and model of your motherboard, as you are going to need to download drivers for audio, video and at least a nic driver or else your windows installation will not perform as well as it should. Most modern motherboards, print out the model number somewhere on the screen while booting up. When you first get a displsy press the Pause/Break key on your keybaord, this will stop the system from booting while you look to see if you can find a model number. Once you are ready to continue just press the Space Bar and it will continue on.

Jim

---

