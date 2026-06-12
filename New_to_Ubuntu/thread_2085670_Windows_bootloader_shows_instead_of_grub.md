---
title: "Windows bootloader shows instead of grub"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Athquiz on 2012-11-18
I've recently tried to upgrade my original wubi installation with a full USB installation. My computer originally came with windows 7, and I sectioned off a 300gb partition to install ubuntu. The installation seemed to work fine. I set up a separate small partition (during installation) for /boot. When I restarted, I got the windows bootloader with Windows 7 and Ubuntu, but the ubuntu wouldn't boot (giving me some error about wubi). I understand that it should normally try to boot with grub, but I didn't get a grub prompt or anything.

Any ideas?

---

### Post by oldfred on 2012-11-18
Best to see details of your installs:

       Post the link to the BootInfo report that this creates.


   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Athquiz on 2012-11-18
The boot repair seems to have fixed my problem. Made a new grub, and booted into ubuntu successfully. Thank you.

---

