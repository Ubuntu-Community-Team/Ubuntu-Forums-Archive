---
title: "Using Ubuntu and an old computer as a print server"
date: 2018-12-10
forum: New to Ubuntu
---

### Post by dave6 on 2018-12-10
I have a brand new old computer sitting here, it came with XP64 bit on it and had never been used, I half made it into a NAS unit but never used as that.

Computer spec is Fujitsu Siemens Esprimo, with Intel P4 cpu and 2gb RAM and a couple of Sata hard drives.
Printer is a HP designjet Z2100.  "Large format printer" 

This printer is housed 40 mile away, where it will be staying.

So, with the above in mind, any tips or recommendations on what software to install on it?

I am not going into details why the printer is that distance from me, but have planned to put the above computer onto or into the printing system.

Dave

---

### Post by mastablasta on 2018-12-10
if you really need or could use a printing computer/server, then it would be better to get something like a raspberry pi for it. it would use a lot less power. if printer is already connected to a PC then i am not sure why you would need to add aditonal PC just to print on it.

but let's say that you do need a specialized PC and lets say your idea is the most cost effective one for you, then you would need at least printer drivers installed (hplip) and some network software (openSSH or similar) to connect to the PC.

---

### Post by dave6 on 2018-12-10
Hi mastablasta,, na the printer is just sitting in the corner of the room unused, so why a print server, I need to upload "FTP" from my computer here which is calibrated, correctly edited photographs to be printed on fine art paper of MY choice, there to the ?? for printing "there being 47.3 mile by car"
My way of thinking would be to use the computer sitting here, bring it there, plug it in and run an Ethernet cable from the router to the computer and download the photographs onto it "the computer" which will have the drivers for the HP designjet Z2100 installed

Does that make it sound more logical ?
Dave

---

### Post by SeijiSensei on 2018-12-11
If you're going to take the physical route, why not USB drives?  A lot more portable than a whole computer.

Is the printer visible to you over a network?  What OS is running on the remote print server?  Does the printer, or its server, have a public IP address?  If so, try opening \\ip.addr.of.printer\ in Windows file manager.

Do you have a well backed-up server already that archives your work?  If not, you could consider using that XP64 machine as a file server.  You don't really need to make it into a "NAS."  Just use the file-sharing already built into Windows.  Export a directory from the XP machine and mount it on your local workstation.

I'd add an external hard disk as secondary backup.  I run a backup program each night that collects files from three remote virtual machines and writes those and some local backups to both the local machine's hard drive and to this external USB device: [https://www.newegg.com/Product/Product.aspx?Item=N82E16822178817](https://www.newegg.com/Product/Product.aspx?Item=N82E16822178817)

---

