---
title: "Grub2 + Encrypted LVM"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by cipherc233 on 2014-03-12
I recently installed Ubuntu Gnome 14.04b about a month ago. In that time I have fallen for Ubuntu, and have even deleted my entire windows partition!
 I installed kali linux a couple of days ago (I know this is not for linux beginners, but it is something that I want to learn and it is the best way for me to start.) using the encrypted lvm option.
 Long story short I wanted my Grub2 back so I updated it under my Ubuntu partition. Now, I can not boot into kali, nor will grub2 even detect it when i run a grub update.
 I have tried everything that I can think of, and I cant find anything online that works. 
Can anyone help? Thanks for the time!

---

### Post by oldfred on 2014-03-13
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If Kali is not a standard ext4 partition, you may need to add drivers to Ubuntu and mount partition so sudo update-grub can see it. Very common with Fedora and its LVM type installs.

---

