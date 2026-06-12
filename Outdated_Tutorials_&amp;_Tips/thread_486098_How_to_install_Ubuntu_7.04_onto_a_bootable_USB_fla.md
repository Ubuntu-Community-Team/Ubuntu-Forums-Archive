---
title: "How to install Ubuntu 7.04 onto a bootable USB flash device"
date: 2007-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by roystondh on 2007-06-27
[SIZE="3"]Firstly I would recommend using the Ubuntu LiveCD for a few days in order that you can familiarise yourself with the operating system, and ensure that it supports your graphics card and any hardware you wish to use satisfactorily before installing it on the flash device.

**In order to undertake the installation you will require the following:- **

**a/ **A PC that supports booting from USB devices and CD-ROM (check within the BIOS settings)

**b/ **A USB flash drive of 4GB or greater (the operating system takes around 2.3GB and a swap file is also required) – Ideally the device & USB port should be USB 2.0 compliant to allow for faster loading. You do not need to prepare the flash drive in any way (formatting and partitioning take place during the Ubuntu install)

**c/ **A Ubuntu 7.04 Live CD (this was tested on the 64bit edition, should be fine with the 32bit edition also)

**The installation process:-**

**1/ **Firstly physically disconnect the systems hard drive(s) – if you disable the hard drive(s) in the BIOS the operating system will still be able to detect the hard drive which increases the risk of installation errors or overwriting partitioning or boot records (other operating systems are not as clever be warned)

**2/** Insert the USB flash drive into a USB port, also I would recommend disconnecting any other USB devices that might have memory as well (e.g. Camera’s connecting via USB)

**3/**From within the BIOS set the system to boot from CD then USB

**4/**Insert the Ubutu LiveCD and boot the machine into Ubutu from the liveCD

**5/**Hit the installation Icon

**6/**Follow the Stages 1 – 4

**7/**At stage 4, partitioning, manually configure 2 partitions - 3.5GB (ext3)  and 0.5GB swap file

**8/**Continue to Stage 7

**9/**Allow around 30-45 mins for the USB drive to be formatted, partitioned and Ubuntu installed (remember writing to flash devices is slower than reading)

**10/**On completion reboot the system, removing the LiveCD

**11/**Upon booting into Ubuntu you should find that a message pops up in the top right hand corner advising you of updates, proceed and install these

**12/**Power down the system and re-connect any disconnected hard drive(s)

You should now be able to simply boot into Ubuntu by inserting the USB flash drive into the system as required and setting boot sequence appropriately in the BIOS

*(Written with thanks to bodhi.zazen and C.S.Cameron who guided me through the process which I could not find well documented on the Ubuntu site)*

**This guide is written with no formal support by myself, and should be undertaken at your own risk, [COLOR="Purple"]*remember always back up anything that you cannot afford to lose*[/COLOR].[/SIZE]**

---

### Post by small_bigguy on 2007-08-04
I May try this, it sounds like a great idea, I can then use ubuntu on any pc i like rather Than windows :D

---

