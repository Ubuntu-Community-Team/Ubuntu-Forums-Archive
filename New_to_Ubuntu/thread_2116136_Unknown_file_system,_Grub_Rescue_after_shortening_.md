---
title: "Unknown file system, Grub Rescue after shortening windows partition"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by nate7 on 2013-02-14
Hi, i've just updates to ubuntu 12.04.2 and i wanted to download Team Fortress 2 for linux. I didn't have enough space to put it, so i decided that i needed to extend my logical partition, which was home. So firstly i had to shrink the windows partition, and i did. Upon restarting i got "error: unknown file system grub rescue" and there it lets me type anything.

I do have a ubuntu live CD, as i'm using it right now to post this. 

Any help would be greatly appreciated. 

Thanks :D

EDIT: Btw i've found this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Wondering if this would help me?

---

### Post by oldfred on 2013-02-14
Welcome to the forums.

Any change to Windows requires Windows to run chkdsk. Did you resize Windows from inside Windows with its disk tools and then reboot so it can run chkdsk. 

But that should not have changed grub in the MBR or changed your / (root) partition.

Best to see what is where. You can download this into your liveCD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by nate7 on 2013-02-14
I used a partitioning software, and upon restarting i got the error. 

Bootinfo = [http://pastebin.com/yf3d4k2z](http://pastebin.com/yf3d4k2z)

Edit: And yes i resized it from within windows

Edit2: I used EASEUS Partition Master

---

### Post by oldfred on 2013-02-15
Did you run the Boot-Repair fixes?

Is says your grub in the MBR is looking for your installin sda6 which is swap and Boot-Repair will reinstall grub and use sda5.

Or you can manually reinstall.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by nate7 on 2013-02-15
I will do the boot repair and get back to you asap

---

### Post by nate7 on 2013-02-15
What do i do here? 

[screenshot attached]

---

### Post by oldfred on 2013-02-15
With BIOS boot, you normally install grub to the drive or sda, sdb, sdc etc. 
Almost never to a partition like sda1, sda2 etc. 
And never to a NTFS formatted partition.

For those with UEFI it should default to the efi partition regardless of what screen says. (Screen may not be updated for UEFI installs).

---

### Post by nate7 on 2013-02-15
Okay, it said it successfully completed. And it gave me this link 

[http://paste.ubuntu.com/1659286/](http://paste.ubuntu.com/1659286/)

I'll reboot and see what happens.

---

### Post by nate7 on 2013-02-15
Awesome! Everything is fixed. Thanks!

---

### Post by oldfred on 2013-02-15
Glad it is booting.

Is everything ok? There seemed to be some warnings and updates may be needed.
Not sure I have ever in my life seen this error:
> falling back to frontend: Teletype

Since Teletype has been out of business for 20 or so years.
(tty is still used as abbreviation in many apps.)

---

