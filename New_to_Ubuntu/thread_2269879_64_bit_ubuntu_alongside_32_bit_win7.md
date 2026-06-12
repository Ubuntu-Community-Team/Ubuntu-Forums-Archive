---
title: "64 bit ubuntu alongside 32 bit win7?"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by nhyrum on 2015-03-18
I have a 32 bit windows 7 enterprise desktop and i am curious if I can install 64 bit ubuntu as a dual boot?I know that some hardware pieces are not 64 bit compatable, but dont know what i have. is there a way i can find out if it is 64 bit compatable and if it isnt will my desktop lock up if i try to install 64 bit ubuntu?

---

### Post by nerdtron on 2015-03-18
What is your CPU model? you can find it on the windows 7 computer properties. Then we can find out if it is 64bit capable.
Most desktops nowadays can support 64bit.

---

### Post by nhyrum on 2015-03-18
amd athalon 64 x2 dual core processor 5000+ 2.6GHz

---

### Post by nerdtron on 2015-03-18
It says 64 so it's 64 bit capable. Although the cpu is a bit older, it is still capable. And how much RAM do you have? If you have 1GB-2GB, then you computer would run faster if you try Xubuntu 14.04

---

### Post by nhyrum on 2015-03-18
it says i have 2 gb ram. good to know i can run ubuntu! always been a fan

---

### Post by Mark Phelps on 2015-03-19
> i can run ubuntu! Read again ... you were told "Xubuntu" not "Ubuntu".  Ubuntu uses the Unity desktop and with an older processor and only 2GB of RAM (some of which might be dedicated to video RAM), you will likely get poor performance running Ubuntu.

---

### Post by mattharris4 on 2015-03-20
> **Mark Phelps said:**
> Read again ... you were told "Xubuntu" not "Ubuntu".  Ubuntu uses the Unity desktop and with an older processor and only 2GB of RAM (some of which might be dedicated to video RAM), you will likely get poor performance running Ubuntu.

I can attest to this.  90% of websites, programs, etc. will work fine with 2GB of RAM running Ubuntu or Edubuntu but that ten per cent that do not will put you into swap which IME slows computers to a crawl on a Linux system.  I have limited experience with Xubuntu but what experience I do have showed me that it will run fine on 2GB of RAM.  Lubuntu requires even less RAM (and processor power).  Since the GUI of those two programs are vastly different I would create a bootable CD or USB of both, try them for a bit booting from the CD or USB without installing then installing whichever one you like best.  As long as your computer is Windows compatible (you do not have to leave Windows on the computer, I also cannot say how Linux will function on Apple hardware as I haven't used any in the past 20 years), don't have really old hardware (more than ten years old or so, not likely with 2GB of RAM), have any NVIDIA parts on the computer or a UEFI BIOS (not likely unless the computer came with Windows 8 or 8.1, if it did please search for UEFI instructions on the Ubuntu support site before installing) and you use the guided install you should be OK.

I am typing this on a seven year old Pentium 4 computer using Edubuntu (Ubuntu with an additional suite of educational programs meant for professors, teachers and students), it runs just fine especially after upgrading the RAM to 3.5GB (it went into swap on a couple of RAM-hog sites I use regularly with the 2GB it came with).

Regarding UEFI, I recently installed Lubuntu on my new 2014 Toshiba laptop (came with Win 8.1 and UEFI) and it installed without any issue by following the UEFI install instructions.  However others have had issues with various brands so if this affects you please do your research before installing any Linux on your computer.

Good luck and hope your Linux install is smooth and uneventful.

---

