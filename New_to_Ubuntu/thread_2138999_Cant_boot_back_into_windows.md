---
title: "Cant boot back into windows"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by AtsNexus on 2013-04-25
Hello there!
Im new to Linux, I tried it out and then i installed it. i made a partion on windows 8, Used Usb universall installer and installed it on The partion. When i try to boot, It doesnt recognize any partition, Just the whole HDD and when i boot up it just boots into linux. Im using Linux 12.10. Help me please? My mobo is ASUS maximus V formula
Thanks

---

### Post by mkstallings1 on 2013-04-25
Do you have a GRUB bootloader screen?  I wonder if going into terminal and typing "sudo update-grub" would help.

---

### Post by oldfred on 2013-04-26
If the sudo update-grub does not work.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by AtsNexus on 2013-04-27
I couldnt install the Boot repair even though i tryed every method. What im going to try to do was boot from my External HDD and erase the partiotion in my hard disk drive. I tried this and i cant, It says the disk is still mounted and i cant delete it. What is grub? Please help me out
Thanks

---

### Post by mkstallings1 on 2013-04-27
You can burn the .iso of Boot Repair to a CD and use it as a live cd to repair GRUB.  I have done this many times.

---

