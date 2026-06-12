---
title: "Installing ubuntu on second hard drive"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by pieman1983 on 2008-08-14
Hello, I am new to linux and just wanted to know how to go about installing ubuntu on a a secondary hard drive as my primary hard drive is running Windows XP. Also after I install it, how would I go about loading up which OS I want? Thanks

---

### Post by nicedude on 2008-08-14
You need to be very careful when doing this since you can easily make your system not work ( at least the XP part ). Instead it is easy to boot the live Ubuntu CD and use the partition editor ( System -> Administration -> partition editor ) and resize your XP partition smaller and then you will have room to install Ubuntu. I don't know if they have an official minimum for Ubuntu but I would suggest somewhere between 15G - 30GB so that you will have plenty of room for anything you want. I like using 25GB XP 25GB Linux and the rest of my space as data storage ( which you could format as FAT32 or NTFS for easy access from both OS's - 4GB max per file limit in FAT32 though so keep that in mind ). This way I can have media like music & video stored on my data partition and still access it easily from either.

The reason installing to 2nd disk is harder is that Ubuntu (or any linux) overwrites the MBR ( master boot record currently populated with Windows MBR code ) with GRUB ( grand unified bootloader ) code and if you don't do it just right you will end up with big hassles trying to get XP to boot again. So either read up on GRUB till you understand how it works or just take the easy route and resize XP partition with live disk and make some free space as this will work much more reliably.

hope this helps you

---

### Post by Bodsda on 2008-08-14
> **nicedude said:**
> You need to be very careful when doing this since you can easily make your system not work ( at least the XP part ). Instead it is easy to boot the live Ubuntu CD and use the partition editor ( System -> Administration -> partition editor ) and resize your XP partition smaller and then you will have room to install Ubuntu. I don't know if they have an official minimum for Ubuntu but I would suggest somewhere between 15G - 30GB so that you will have plenty of room for anything you want. I like using 25GB XP 25GB Linux and the rest of my space as data storage ( which you could format as FAT32 or NTFS for easy access from both OS's - 4GB max per file limit in FAT32 though so keep that in mind ). This way I can have media like music & video stored on my data partition and still access it easily from either.

The reason installing to 2nd disk is harder is that Ubuntu (or any linux) overwrites the MBR ( master boot record currently populated with Windows MBR code ) with GRUB ( grand unified bootloader ) code and if you don't do it just right you will end up with big hassles trying to get XP to boot again. So either read up on GRUB till you understand how it works or just take the easy route and resize XP partition with live disk and make some free space as this will work much more reliably.

hope this helps you

This is just not true. Installing Ubuntu on a second hard drive (assuming it has no needed data on it) could not be easier. If it has data on it which you wish to keep it is still possible and relatively simple.

Boot up the live cd and start the install.
  When you get to the partitioning stage there will be a few options to choose from. Choose 'Guided. Use continuous amount of free space' and make sure you get the correct hard drive.

This will install ubuntu onto your second hard drive and install the Grub bootloader onto the correct mbr. After the installation has complete reboot and you will see the bootloader, from there you can choose Ubuntu or Windows.

Hope this helps

Bodsda

---

### Post by nicedude on 2008-08-14
It is true as I have seen people do silly stuff and make their system unusable ( by not reading what they are doing before doing it ). For example I helped a gentleman here a few months ago that installed ubuntu to a second portable hard drive thinking it would be a cool idea. He somehow ended up with his first hard disk's MBR ( which did contain Windows MBR code ) overwritten with GRUB but the rest of his GRUB ( such as his menu.list file ) ended up on the portable and when he was done he ended up with a jumbled up mess that wouldn't boot without the portable plugged in and somehow it still wouldn't boot to XP just Ubuntu. So I once again say it is more problematic than dual boot on the same physical drive, as there are more variables to get jumbled up.

Not impossible, Not difficult ( If you read directions ) - But if you just jump right in willy nilly then you might be unpleasently supprised when things don't turn out as envisioned. Just read up on installs before you try to do any certain method.

---

### Post by pieman1983 on 2008-08-14
Alright guys. Thanks for all your help. I guess I'll go get my feet wet with linux now.

---

