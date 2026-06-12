---
title: "Server Installer Won't Recognize sda"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by BobMarso on 2012-07-20
I am trying to install Ubuntu Server 12.04 on the following system: Intel DP35DP motherboard, two Seagate 1TB drives (sda and sdb), two Seagate 1.5TB drives (sdc and sdd), and one 3TB Seagate drive (sde).  Using GPartEd from the Desktop Live CD in the "try without installing" mode, I have written a new MSDOS partition table to each 1TB drive and created one primary partition and one extended partition.  In the extended partition I have place logical partitions for Ubuntu Server.  All partitions on both drives have the raid flag set and the intended boot logical partition has its boot flag set.

I then restart the computer with the server installation CD.  The computer starts up, goes through the language, network, and user setups, I tell it to recognize the RAID function, and then does the "detect drives" step.  However, only sdb, sdc, sdd, and sde are recognized.  The installer does not recognize sda.  At this point I can set up a RAID0 with sdc and sdd, but I can't set up a RAID1 for the Ubuntu installation using sda and sdb since it won't recognize sda.  Any ideas why?  Why is the Desktop version of 12.04 able to recognize all drives but the server installer can't see sda?

Thanks for the help

---

