---
title: "LinuxFromScratch won't boot"
date: 2007-02-04
forum: Other OS Talk
---

### Post by presbp on 2007-02-04
I have tried downloading the LFS LiveCd from 2 different locations and tried burning each ISO.  When I boot it comes to the Linux from Scratch splash screen and tells me to hit enter to boot normally or hit F1 for boot options.  
I have tried just hitting enter to boot normally from both ISOs and tried hitting F1 on both of them.  

When I hit F1 it gives me what to type to boot the LiveCd in a certain resolution, boot it to a certain timezone and how to tell it how to use the linux.ata kernel image to recognize SATA CD/DVD drives and how to use the 64-bit linux kernel image to boot w/ 64-bit PCs.  I tried the linux.ata but that didn't work either. ** All times it said it could not find the LFS LiveCD in any drive.**

I have an Asus P5B Deluxe/Wifi-AP motherboard with an Intel P965 Express Northbridge and a Intel ICH8R Southbridge.  

There is a JMicron RAID controller onboard and in Windows to get the drives to be recognized as anything more than read-only drives (I could not burn with them) I had to install a JMicron RAID controller and then update the driver on the JMicron RAID device, then the JMicron device disappeared from under the SCSI and RAID devices and Standard Dual Channel IDE Controller appeared under IDE ATA/ATAPI devices and then the drives started working.  

Also when trying to boot Puppy Linux from the LiveCD it said it couldn't find the Puppy boot media.  

It seems that my drives are IDE devices but since the JMicron RAIN controller controls the devices that while they are IDE some programs think they are SATA or either it can't decide what kindof drive it is.

---

### Post by bonzodog on 2007-02-05
This is a well known bug that, as you can see, even MS cannot solve themselves. JMicron Controllers are a PIA, and will only work after the installation of certain drivers. 

The only way around this, to get CD's to boot the machine is to use a standard IDE CD-ROM to boot from, on the ata port, or get a SATA HDD, and drop that on the SATA port, so both drives are on the same protocol. This could be an extensive bit of work though, and it does seem insane, but it is your JMicron controller thats getting in the way, and Linux does not by default include the driver for it - it normally has to be added after install.

---

### Post by presbp on 2007-02-06
so is there a way to get this problem fixed without a huge amount of time and effort spent without having to get an external drive?

---

