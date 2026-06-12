---
title: "Gave up waiting for root device"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by shoebansari on 2011-11-12
Hi! I'm new to ubuntu.. An absolute beginner!

Well. I tried to install Ubuntu 11.10 by using wubi.

It copied along well, and i was asked to reboot - And when i rebooted, there were dual choice - Windows XP and Ubuntu.

When i selected ubuntu, I got this following message:

Gave up waiting for root device - Common problems are
-Boot args (cat/proc/cmdline)
 -Check rootdelay=(did the system wait long enough?)
 -Check root=(did the system wait for the right device?)
-Missing modules (cat/proc/modules; is/dev)
ALERT! /dev/disk/by-uuid/8c44-4dba does not exist. Dropping to a shell.

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter help for a list of commands.
(initramfs)_

System:
Windows XP Professional , 1GB RAM.

Please help me out.:confused::confused: And do remember I am a beginner!:lolflag:

---

### Post by bcbc on 2011-11-12
Hi, welcome to the forums. What computer brand/model and graphics card do you have? How did you install? - did you download just wubi.exe or did you run it from a CD?

---

### Post by shoebansari on 2011-11-20
I downloaded wubi.exe, and set apart 10GB for Ubuntu installation in the drive F.

Here is my computer data.

Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.100216-1441)
           Language: English (Regional Setting: English)
System Manufacturer: INTELR
       System Model: AWRDACPI
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: Intel(R) Pentium(R) 4 CPU 2.40GHz
             Memory: 1016MB RAM
          Page File: 653MB used, 1791MB available
        Windows Dir: C:\WINDOWS

Here is the info for the graphics card.
 Card name: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
     Manufacturer: Intel Corporation
        Chip type: Intel(R) 82845G Graphics Controller

---

### Post by Rubi1200 on 2011-11-20
Hi and welcome to the forums :-)

Try this and let us know if it works:

Download the desktop ISO:
[ubuntu-11.10-desktop-i386.iso]("http://releases.ubuntu.com/oneiric/ubuntu-11.10-desktop-i386.iso")

Download the executable:
[wubi.exe]("http://releases.ubuntu.com/oneiric/wubi.exe")   

Place them both in the same folder, e.g. on the Desktop, and then run the executable file.

---

### Post by shoebansari on 2011-12-03
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Try this and let us know if it works:

Download the desktop ISO:
[ubuntu-11.10-desktop-i386.iso]("http://releases.ubuntu.com/oneiric/ubuntu-11.10-desktop-i386.iso")

Download the executable:
[wubi.exe]("http://releases.ubuntu.com/oneiric/wubi.exe")   

Place them both in the same folder, e.g. on the Desktop, and then run the executable file.

Dear rubi, 
i followed your advice.. I downloaded both, placed both in a folder and installed. It went without a hitch. But that is when the real problem starts - Ubuntu booted fine, to complete the installation. But meanwhile, a message came up, saying "that ubuntu/disks/root.disk does not exist! Please check your partitions by using the partition menu."

What could be the problem?

---

### Post by lolpenguin on 2011-12-04
> **shoebansari said:**
> Dear rubi, 
i followed your advice.. I downloaded both, placed both in a folder and installed. It went without a hitch. But that is when the real problem starts - Ubuntu booted fine, to complete the installation. But meanwhile, a message came up, saying "that ubuntu/disks/root.disk does not exist! Please check your partitions by using the partition menu."

What could be the problem?

The disk file C:\ubuntu\disks\root.disk, the main disk used for the Wubi install does not exist. Uninstall Wubi:
Windows Vista/7
Control Panel>Programs and Features>Ubuntu
Windows XP/earlier
Control Panel>Add or Remove Programs>Ubuntu

Then retry Rubi1200's method.
Service Pack 3 is recommended, but I don't know if this affects the issue.

---

### Post by shoebansari on 2011-12-04
> **lolpenguin said:**
> The disk file C:\ubuntu\disks\root.disk, the main disk used for the Wubi install does not exist. Uninstall Wubi:
Windows Vista/7
Control Panel>Programs and Features>Ubuntu
Windows XP/earlier
Control Panel>Add or Remove Programs>Ubuntu

Then retry Rubi1200's method.
Service Pack 3 is recommended, but I don't know if this affects the issue.

Dear lolpenguin,
Many thanks for your help - I followed just as you said. There was a rootdisk from my previous Ubuntu installation (11.04, since uninstalled). Your method removed that root disk, and I was able to boot up Ubuntu successfully!
Many thanks once again, and I appreciate all help received from this forum.  :D
And, yes I forgot - SP2 or SP3 doesn't matter! It installed fine on SP2.

---

### Post by lolpenguin on 2011-12-04
Good to hear!
Don't forget to marked threads as "solved" when they are: it's under thread tools.

---

### Post by Rubi1200 on 2011-12-04
I'm also pleased to hear things worked out :)

As requested, mark this Solved using the Thread Tools near the top of the page.

---

### Post by zdc26z on 2013-02-27
I've been fighting with this for a few days.  This worked like a charm, thank you!

---

