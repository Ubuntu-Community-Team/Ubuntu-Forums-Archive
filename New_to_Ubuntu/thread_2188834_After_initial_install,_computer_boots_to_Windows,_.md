---
title: "After initial install, computer boots to Windows, never see GRUB"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by ixjctx on 2013-11-19
So, I'll just put this out there to start, I am brand new to Linux and Ubuntu. The extent of what I know is comprised of the last 3 or so hours randomly searching the web to try and solve my problem.

It all started when I choose to install Ubuntu 13.10 alongside Windows 8.1 (which was an upgrade from the Pre-Installed Windows 7). When it asked me to partition, the only option it gave as to which harddrive to use was my second hard drive (I have two in this computer, the first is 500GB and has my Windows OS, the second is the one mentioned before and is 1TB). I was ok with this until it gave me a fatal error about a failed grub install and asked me to assign it somewhere else. Over the past couple hours I have tried reinstalling Ubuntu and changing the Grub location many times including to a location on my second hard drive.

My question is this, either how can I get my computer to boot Grub or how can I assign grub as a boot method in BIOS.

Any help is appreciated greatly. 


NOTE: When I restart my computer, it boots to Windows, I get into Ubuntu using a LiveUSB.

---

### Post by oldfred on 2013-11-19
Best to see details.
Once you get grub installed to sdb, set BIOS to boot from sdb.
Also Boot-Repairs auto fix will install grub to both drives. Do not run that as you really want to keep Windows boot loader on Windows drive and grub on Ubuntu drive. You can uncheck auto fix and check update MBR and choose Ubuntu and sdb as location to install boot loader.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

