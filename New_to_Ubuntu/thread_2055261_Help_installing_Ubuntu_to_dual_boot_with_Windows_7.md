---
title: "Help installing Ubuntu to dual boot with Windows 7"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by bluescreenedgamer on 2012-09-08
Hey everyone. I am having a little trouble installing Ubuntu 12.04 to dual boot with Windows 7. I have tried it two ways. I have tried to install it using Wubi, but when i boot it, i get stuck at a GRUB prompt. I have also tried to install it using a USB stick. I got all the way to clicking install, but instead of letting me install alongside Windows 7, it says that no operating system is detected. My two options from this screen are a clean install, or to choose where to install it.

Does anyone have any remedy for either of these issues? Or a better way to install it? Any help is greatly appreciated!

Thanks

---

### Post by lincoln32 on 2012-09-09
Wubi fails from time to time
1.install virtual box the install ubuntu 12.04 in vitual box
2. defrag windows then use windows 7 to srink a drive to make room for ubuntu. Make sure there are no more than three partitions because some win 7 installs use all 4 partitions then you would need to delete one like the recovery partition. then boot to a live ubuntu and install to the unused or side by side option and you should be fine):P

---

### Post by Martwana on 2012-09-09
> **bluescreenedgamer said:**
> Hey everyone. I am having a little trouble installing Ubuntu 12.04 to dual boot with Windows 7. I have tried it two ways. I have tried to install it using Wubi, but when i boot it, i get stuck at a GRUB prompt. I have also tried to install it using a USB stick. I got all the way to clicking install, but instead of letting me install alongside Windows 7, it says that no operating system is detected. My two options from this screen are a clean install, or to choose where to install it.

Does anyone have any remedy for either of these issues? Or a better way to install it? Any help is greatly appreciated!

Thanks

Hi, i am relatively new to Linux in general. When I tired to install alongside windows 7, the Ubuntu installer could not recognise the current partition table. 

What to do is, load up the live cd or USB, and opn gparted. Then create your Ubuntu partition there and then try the installer, and it might recognise the new partition. 

If this does not work, your will have to do it the same way I did, backup your data, and use the gparted to create a new partition table. Yur new table should have unformatted space at the start of your hdd for windows 7 and the size you want, and a ext4 partition after it for ubuntu.Then, install windows 7 first, install it to the unallocated space you made in gparted, get it set up, but don't restore your data just yet. 

Then install Ubuntu, it should go fine if you pick the new ext4 partition, and make sure the bootloader installs to the hdd itself and not the usb if your using one. 

That method worked fine for me, at the inconvenience of backing up and restoring my data, I didnt mind as I do plan to migrate to Ubuntu.

---

### Post by Bashing-om on 2012-09-09
@ all;
           Windows tools for windows problems, Linux tools for ubuntu situations.
lincoln32 has the better approach: use windows to set up the space for the ubuntu installation (prevents  possible data corruption).

[INDENT]just my opinion <==BDQ

[/INDENT]

---

### Post by hwyckoff on 2012-09-09
> **bluescreenedgamer said:**
> Hey everyone. I am having a little trouble installing Ubuntu 12.04 to dual boot with Windows 7. I have tried it two ways. I have tried to install it using Wubi, but when i boot it, i get stuck at a GRUB prompt. I have also tried to install it using a USB stick. I got all the way to clicking install, but instead of letting me install alongside Windows 7, it says that no operating system is detected. My two options from this screen are a clean install, or to choose where to install it.

Does anyone have any remedy for either of these issues? Or a better way to install it? Any help is greatly appreciated!

Thanks
I recently installed Ubuntu on my computer as a dual boot.  Wubi didn't work well for me, so I uninstalled that and installed Ubuntu 12.04 as a CD install. I choose the dual boot option.  I also had to make sure that the Ubuntu version I installed was correct for my computer (AMD64).  Which architecture do you have?  Intel 32 bit or AMD 64?

---

### Post by Martwana on 2012-09-09
> **Bashing-om said:**
> @ all;
           Windows tools for windows problems, Linux tools for ubuntu situations.
lincoln32 has the better approach: use windows to set up the space for the ubuntu installation (prevents  possible data corruption).

[INDENT]just my opinion <==BDQ

[/INDENT]

Yea I tried that, a few different forums gave me suggestions for mine, but there was just something about my partition table that the Ubuntu installer just didn't like. 

I agree, keep the 2 separate if you can, but my method worked successfully in my case, so I have to share that if I think it may help another.

---

### Post by Mark Phelps on 2012-09-10
The main problem with using Linux filesystem tools to shrink down Win7 partitions to make room for Ubuntu is that, all too often, that results in filesystem corruption of the Win7 OS partition -- rendering it unbootable and VERY difficult to then fix.

So, experimenting with using GParted to shrink down Win7 OS partitions carries a very high risk.

Which is why some of us say -- Windows tools for windows filesystems, Linux tools for Linux filesystems.

---

