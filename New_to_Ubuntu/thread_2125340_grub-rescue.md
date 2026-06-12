---
title: "grub-rescue"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Sly14Cat on 2013-03-13
Hello,
I've been wanting to install Debian to my Laptop but it already has 4 partitions: Windows, Dell OEM, Recovery and Ubuntu. I've decided to remove my Recovery partition but the problem is that when I added Ubuntu back to the list of OS'es it says the partition it's on can not be found and brings me to grub-rescue, what do I do from there? Is there a certain command?

---

### Post by oldfred on 2013-03-13
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

