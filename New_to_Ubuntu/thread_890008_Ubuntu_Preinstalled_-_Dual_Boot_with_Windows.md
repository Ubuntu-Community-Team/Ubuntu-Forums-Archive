---
title: "Ubuntu Preinstalled - Dual Boot with Windows"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by X40nick on 2008-08-14
Hi, 

I have been interested in buying a Dell XPS M1330n with Ubuntu preinstalled, but unfortunately I do require XP Professional. Is there any way I can:

1. Install Windows, by shrinking the Ubuntu parttion to around 60GB, and keeping around 100GB for Windows? 
2. Not changing the boot loader, just simply adding Windows? 

--OR--

1. Reinstall Windows by using the entire HD.
2. Then install Ubuntu? Does Dell do any magic to the XPS M1330n to make everything work out of the box? 

Basically, I want to buy the Ubuntu version, but install XP, whilst keeping a Ubuntu partition? 

Is that possible, and if possible can it be done easily, I am not the best computer user, and please keep instructions very basic!!!

Many thanks for reading, I look forward to your replies!

Best Regards,

Nick

---

### Post by X40nick on 2008-08-14
Might go for the Inspiron 1525 insted here are the specs:

Base  	Intel® Core™ 2 Duo Processor T8100 (2.10 GHz, 800 MHz FSB, 3 MB L2 cache) - N-Series
Memory 	2048MB 667MHz Dual Channel DDR2 SDRAM [2x1024]
Keyboard 	Internal Keyboard Uk/Irish (QWERTY)
Video Card 	Integrated Intel® Graphic Media Accelerator X3100
Hard Drive 	120GB (5400rpm) SATA Hard Drive
Modem 	Dell™ v92 Data/Fax Modem - UK
Optical Devices 	8x DVD+/-RW Optical drive - N-Series
Wireless Networking 	Intel® Pro Wireless 3945 802.11a/b/g Mini-Card - Europe - Core 2 Duo Processors
Cables 	Power Cord UK 1meter
Shipping Documents 	English EMEA 1 Documentation
Gedis Bundle Reference 	N0852515
Microsoft Application Software 	No Software Application
Standard Warranty 	1Yr Limited Warranty - Collect & Return
Enhanced Service Packs 	1 Year Base Warranty
Power Supply 	65W AC Adapter
Order Information 	Inspiron Order - UK
Primary Battery 	6-cell battery
Carrying Cases 	No Carry Case
OS-Linux 	Ubuntu Edition version 8.04
Dell System Media Kit 	No Resource CD
Camera 	Web Camera NOT included
Colour Choice 	Ruby Red Colour with Microsatin Finish
Accidental Damage Support 	No Accidental Damage Support
Online Promotion Option for GEDIS Configs 	Dell Internet Order
LCD 	15.4" Wide Screen WXGA (1280 x 800) Display with TrueLife™

Can I do the same thing, just with that notebook?

Thank you.

Nick

---

### Post by Troll_the_Great on 2008-08-14
I would suggest to install Windows first, otherwise you will have problem with the GRUB menu.
Put a Windows installation disc in your machine, boot from it, and follow the installation instructions (if you never done this before is advisable to ask a fried to help).After you install Windows, create a separate partition (using Partition Magic for example) for your Ubuntu installation.Download the Ubuntu installation from the Ubuntu site, burn it to a CD, and repeat the process I described above:boot from the CD, follow the instruction, and when it asks you for partitioning, choose manual partitioning, then choose the partition you just created as boot (the boot look like "/").
That should be it.You could create a partition with the CD when you install Ubuntu, but I found it easy the way I described it above (this is the way I did it).
Good luck!

---

### Post by X40nick on 2008-08-14
Thank you for your reply! I thought that would be easier, mainly due to the GRUB and partitions. 

Okay, but does Dell do anything special to make all the hardware work? Can I get everything working out of the box when I install it?

Thank you.

Nick

---

### Post by Troll_the_Great on 2008-08-15
> **X40nick said:**
>  
Okay, but does Dell do anything special to make all the hardware work? Can I get everything working out of the box when I install it?

Thank you.

Nick

I can't answer that for sure, but I think it will work out of the box.I have an ASUS  laptop and everything worked out of the box for me (and I have a built in camera and a bluetooth adapter).The only problem I had was with the built in microphone, but I manage to fix it thanks to this wonderful forum.
But to test if your hardware are compatible with Ubuntu there is an easy way:boot from the CD and when the menu appears, choose "Try Ubuntu without any changes to my computer" (or something like that).This option is called "Live CD" and basically lets you run an entire operating system from the CD in your RAM, regardless of what other operating system you have (or don't have) and without affecting it in any way.The downside is that your system will be a bit slower than normal (because it runs in RAM) and any settings will be lost when you reboot.But it's a good method to find out if your hardware are compatible with Ubuntu.Post back any questions you have, and the forum will try to help you.
Cheers!

---

