---
title: "Windows drive now thinks it has Ubuntu installed too"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-01
C: is my Windows drive. I installed Ubuntu on my D: drive.

Now my computer thinks there's an Ubuntu installation on C: as well (it's an option, albeit a non-functioning one, even when D: is disconnected).

How do I smack some sense back into my C: drive without wiping everything and reinstalling Windows?

---

### Post by Impavidus on 2012-12-02
Grub, your boot loader, is on your C drive. Grub knows ubuntu is installed on the D drive and therefore it gives you the option of booting ubuntu. Grub doesn't notice when the D drive is disconnected.

If you want to make more sense of it, you'd best use some windows utility to repair the boot loader. Windows is very happy when it can remove any component of a non-windows OS. You don't have to reinstall windows.

---

### Post by Elect GMax on 2012-12-03
> **Impavidus said:**
> Grub, your boot loader, is on your C drive. 

Well how the heck did it get THERE?

> **Impavidus said:**
> you'd best use some windows utility to repair the boot loader

Like what?

---

### Post by Cheesemill on 2012-12-03
> **Elect GMax said:**
> Well how the heck did it get THERE?
It's the default installation setting. Unless you specify otherwise then grub is automatically installed to the master boot record of the first hard drive (Windows does exactly the same thing with its boot loader).


> Like what?Your Windows installation CD.

---

### Post by Elect GMax on 2012-12-03
> **Cheesemill said:**
> Your Windows installation CD.

Dude, if that was an option right now, I wouldn't be playing with Linux.

---

### Post by oldfred on 2012-12-03
You can use Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
Or manually install lilo which works like the Windows boot loader.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

