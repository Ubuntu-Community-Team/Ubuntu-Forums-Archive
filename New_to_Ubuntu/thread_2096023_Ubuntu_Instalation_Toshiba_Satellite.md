---
title: "Ubuntu Instalation Toshiba Satellite"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Odraude ACS on 2012-12-18
I want to install Ubuntu 12.10 or 12.04 LTS in my Laptop but i don't know wich is the good one for my hardware.

My Laptop:
AMD Turion(tm) X2 Dual-Core Mobile RM-72 2.10 Ghz 64Bits
4 Gb RAM
Ati Radeon 3100
300 Gb Hard Disc

I want to install Ubuntu 12.10 64Bits or 12.04 LTS 64Bits but i don't know if my laptop support them. I heard that Ubuntu is faster than Windows, well i use Windows 7 Ultimate 64Bits and it's fast i don't have problems, but i don't know if my Laptop is the strong enough to support Ubuntu.

I just have one more cuestion.
Wich is the correct partition to install Ubuntu?
I mean:
/
swap
/home

ext4?

Thank you for your time !!

---

### Post by Pjotr123 on 2012-12-18
If 12.04 LTS runs on your machine, then it's the best choice. Otherwise choose 12.10. Reasons: [https://sites.google.com/site/easylinuxtipsproject/version](https://sites.google.com/site/easylinuxtipsproject/version)

Your laptop hardware is certainly powerful enough. No problems there.

Don't worry about the installation; do it simple, like this:
[https://sites.google.com/site/easylinuxtipsproject/installation](https://sites.google.com/site/easylinuxtipsproject/installation)

Good luck!  :)

---

### Post by TheGuyWithTheFace on 2012-12-18
I agree with Pjotr123, Your computer will run fine for either release. whether to install 12.04 or 12.10 really comes to a personal choice. 12.10 is the most recent, so it has the newest features and most up to date applications. 12.04 Is a Long Term Support, so that means it's more stable. (It's what canonical recommends for business users, so you know it's pretty darn stable.) 

For the partitioning and such:

ext4 is the file system that Ubuntu uses. To most users, that doesn't really matter, just know that it's to linux systems like nfts is to windows. 

/ is the base of your system. Wherever that is, the rest of the system, files, applications, everything is in that partition, unless you specify otherwise. Think of it as the C: drive in windows.

A /home partition just means that your personal files are on a separate part of your drive, so if your system gets messed up, your files are in a safe(er) location. 

Swap is a part of your drive that the system uses for RAM if you are multitasking a lot and don't have enough. 4GB of RAM is plenty for your system, so I don't think you'd use more than 1 or 2 GB of swap at the very most. You could probably go without it if you wanted to and never really notice, but it's recommended to have some swap just in case, and it can't really hurt!


The good news? You really don't have to worry about any of the partitioning! When you are in the installer, if you want to specify everything and want to have separate /home partitions or whatever, you can select "Something Else" when it asks you what you want to do for your installation. Otherwise, just select either: "erase drive" or "Install Ubuntu alongside Windows 7", depending on what you wish, and the installer will handle all that stuff for you. :D

---

