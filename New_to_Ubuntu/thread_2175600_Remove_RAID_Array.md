---
title: "Remove RAID Array"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by rgallivan on 2013-09-20
Hello

     So I have a hard drive that is giving I/O errors and can only read data from certain areas of the disk so I thought it was time to replace it and setup a Mirror with 2x 2TB drives.  I have a Asus M4A785-M motherboard that looks to have what everyone is calling Fake RAID now.  After fighting with Ubuntu 12.04 LTS and not being able to get it to see the mirror (it would only show 2 separate disks) I gave up and set the BIOS back to AHCI mode.  However now I have 2 separate disk entries from the old RAID setup that it is still seeing and I can't get rid of them using dmraid or anything.

/dev/dm-0 and /dev/dm-1
Also in /dev/mapper 
pdc_jjgihaecf
pdc_jjgihaecf1
(I think those 2 are the drives it thinks are still in an array)

How do I remove these and go back to normal disks? When I try to format any of the physical disks it comes up saying the drive is busy...HELP!

---

