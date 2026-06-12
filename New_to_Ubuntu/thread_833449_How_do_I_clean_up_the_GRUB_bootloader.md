---
title: "How do I clean up the GRUB bootloader?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Seablue on 2008-06-18
Hi all,

I have my Ubuntu on a dual-boot with Windows Vista Home Premium. After getting many updates for Ubuntu, my GRUB has been crowded with 3 Kernels and their recoveries, memtest86x, and my Vista. How do i clean out the old kernels from the bootloader?

Thanks,
Seablue

---

### Post by stchman on 2008-06-18
> **Seablue said:**
> Hi all,

I have my Ubuntu on a dual-boot with Windows Vista Home Premium. After getting many updates for Ubuntu, my GRUB has been crowded with 3 Kernels and their recoveries, memtest86x, and my Vista. How do i clean out the old kernels from the bootloader?

Thanks,
Seablue

Remove the kernels via Synaptic.  This will remove the GRUB entries.

---

### Post by Kingsley on 2008-06-18
Hey, this link explains what you want better than I can.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

---

### Post by TeoBigusGeekus on 2008-06-18
Go to synaptic package manager and uninstall the oldest kernel.
Then open up your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```
and comment out the previous kernel (add # in front of its entries) but don't uninstall it.
Keeping the previous version of a kernel is highly recommended in case something goes wrong with your system and you need to load an older kernel to have it working again.

---

### Post by logos34 on 2008-06-18
> **teobigusgeekus said:**
> comment Out The Previous Kernel (add # In Front Of Its Entries) But Don't Uninstall It.
Keeping The Previous Version Of A Kernel Is Highly Recommended In Case 


+1

---

### Post by Norradj on 2008-06-18
This the way I have clean the GRUB menu.lst (start menu) since several years with Ubuntu ( I got it long time back from a forum)

This is perfectly OK if you use standard Kernels that you got from Ubuntu uodates.

1. boot with the latest kernel from the boot-list on top and check booting is OK.

2 Go to synaptic and search for "linux" and mark the older "linux image xxx" (you should find all of them there)for completly removal.

3. synaptic will ask for removal of ubuntu modules and restricted modules as well. mark Ok and run command

4. Reboot and you will find that the boot entries in Grub menu.lst are changed and the old entries are removed.

5. conclusion: for dual boot this will work perfectly fine as you don't have to edit the menu.list to change boot order etc.
so if you boot default to other OS they will still boot default.

---

