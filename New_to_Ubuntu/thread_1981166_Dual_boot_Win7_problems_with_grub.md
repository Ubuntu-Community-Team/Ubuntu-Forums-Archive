---
title: "Dual boot Win7 problems with grub"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by language4u on 2012-05-16
Hi all - 

I'm trying to install 12.04 Ubuntu over 12.04 Kubuntu (don't ask - I just missed the simplicity of Ubuntu) on a Win7 dual boot using a liveUSB.

First tried the automated "install over existing Ubuntu" option, but got the "grub rescue >" prompt on boot after install. Tried re-installing using "something else", and found that it had tried to put grub on /dev/sdb, probably my USB. So, I tried puttung grub on /dev/sda, and "/" on /dev/sda5 (sda1 is Win7 recovery, sda2 is win7, sda3 is the swap, and sda4 is not there for some reason). 

Reboot: same problem. 

Do I need to fix the Win7 mbr, re-partition and re-install? Or is there another way? Am I just doing something stupid during the Ubuntu install?

Thanks many times in advance.!

---

### Post by oldfred on 2012-05-16
You should just be installing to sda, if sda is hard drive. Some BIOS promote flash drive to sda and confuse things. 

You can post the Boot-Info link from this and we can suggest best way to repair. You can add it existing Ubuntu installer USB or CD or download a fully bootable repairCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

