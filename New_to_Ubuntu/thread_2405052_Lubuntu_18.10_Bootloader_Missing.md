---
title: "Lubuntu 18.10 Bootloader Missing"
date: 2018-10-31
forum: New to Ubuntu
---

### Post by kksilvery on 2018-10-31
Hi,

I have downloaded 64-bit version of Lubuntu 18.10 from the official website. 

I use Rufus to make bootable USB drive, and I installed Lubuntu via USB. 

However, after installing and removing the USB drive, the Lubuntu doesn't load at all. 

The computer says, no bootable device found. 

I scanned HDD and i installed Windows 7, and Lubuntu 18.04 are working fine, but the latest Lubuntu 18.10 is not working. 

What should I do?

-----------------update - next day----------------
I tried Installing Lubuntu 18.04 and its not working as well. 

This is the error I'm getting on my computer. [Error Image]("https://ibb.co/e2g2A0")

------------ Update 04/Nov/2018------------------------------

I have solved the issue.

**Step 1**: I created 32-bit Windows 7 bootable USB drive and Installed it successfully. 
**Step 2**: I formatted the USB drive to create bootable Lubuntu 18.10 USB drive and installed it alongside Windows 7.
**Step 3**: I formatted the USB drive to create bootable Lubuntu 18.04 Bionic Beaver and wiped the entire HDD to install it. 

Now, I am using Lubuntu 18.04 Bionic Beaver and I gave up on 18.10 Cosmic Cuttlefish.
[B]
Note[/B]:Remove the HDD cables and try to clean it using hair dryer or air blower. 

Overall, happy ending.

---

### Post by yancek on 2018-10-31
If you can boot Lubuntu 18.04, do that and go to the site below and download boot repair using the 2nd option, ppa.  Run it by selecting the option to Create BootInfo Summary and post the link you get when it finishes.  Do NOT try to make any repairs.  Someone should be able to advise you on your next step(s).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kksilvery on 2018-11-01
Hi Yancek,

Sorry mate, no luck! This is the error message I'm getting [Error Image]("https://ibb.co/e2g2A0")

---

### Post by yancek on 2018-11-01
Looks like an older computer.  That looks like a BIOS error message.  Is that the first thing you see when you boot?  Are you able to see the various options (boot and other) on initial boot?  Are you now unable to boot anything, you earlier stated windows 7 and Lubuntu 18.04 booted?

---

### Post by kksilvery on 2018-11-01
Hi Yancek,

Yes, its an old computer from 2007.

I have installed Windows 7 SP1 64bit and its working fine.

However, the Lubuntu 18.04 and Lubuntu 18.10 is not working.

I turn on the computer with Lubuntu 18.04 or 18.10 installed, and I have this error.

I am using the default BIOS settings and it worked fine with Windows 7 and Lubuntu 18.04 (installed it couple of weeks ago.)

---

### Post by vawaid on 2018-11-29
I have the exact same problem, but I'm using a laptop and blowing the HDD port doesn't help.
windows 8 and 10 work just fine.

---

### Post by oldfred on 2018-11-29
@vawaid
An old BIOS system and new UEFI system which Windows 8 or 10 is are totally different. Please post your own thread and include link to Summary Report from Boot-Repair (See post # 2).

---

### Post by kksilvery on 2018-12-13
Vawaid, add your laptop specifications or model number, so I can offer help to you. 

I have fixed my computer in Oct 2018 and I used it a few minutes ago.

---

### Post by buzzlightyear22 on 2019-02-27
I had the same issue with lubuntu 18.10. Solved it using fdisk and setting the boot flag on the partition where lubuntu was installed from the usb installer and rebooting. For some reason the boot flag was not set during installation, I installed twice with same result.

---

