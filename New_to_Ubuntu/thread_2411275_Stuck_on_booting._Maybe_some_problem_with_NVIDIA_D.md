---
title: "Stuck on booting. Maybe some problem with NVIDIA Driver"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by aiesper on 2019-01-28
Sorry Newbie, this is my first time installing Linux
There are those of you who have problems with the NVIDIA driver on Linux? I tried it on two distro (Debian and Ubuntu) but it still stuck on boot.

**Debian**: 
I always get a black screen error message "*Pcie bus error*" or "*pointer to flat table invalid*". Some my friend suggest me to add "*pci = noaer*" to the kernel boot parameter. I try it, but show me another error "*pcie bus error: severity=corrected, type=physical layer*".
A little trial, I added "*nomodeset*" and deleted the "*quiet splash*" in the kernel boot parameter, it successfully entered. I try updating the nvidia driver according to the wiki, I rebooted into the login page and then the white screen, told to try again and get stucked. 


**Ubuntu**: First try, Login successfully. I update packages (apt-get update and apt-get upgrade), also stagnant in Ubuntu without a black screen or error message. I tried to reboot, randomly entered (2x of 10 boot trials). If I try the method when using debian, same black screen and the same error message come out. I tried to use "*fsck*" from a live usb. I tried, entered, my mouse pointer even though the pointer can move but it can't be click everything.


My Spec :
- Intel i7-7700HQ
- GTX 950M
- 8GB RAM

---

### Post by kc1di on 2019-01-28
Hello and Welcome to Ubuntu,

Have you installed the Nvidia driver?  We need to know which Nvidia card your machine has.  If you can get to the desktop please go to a terminal and type this command and 
post the results here: ```
Inxi -Fxz
```

If your still using the Nouveau driver that come stock with the system you'll need to append nomodeset to the grub boot line a boot.  
This [AskUbuntu]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") thread will show you how to do that.

---

### Post by Autodave on 2019-01-28
What driver did you install for the Nvidia card and where did you get it from?

Generally, adding the *nomodeset* will allow you to get into the system until you get the correct driver installed.

You will always want to install the video driver from the repositories: never from the Nvidia site or any other site.

---

### Post by oldrocker99 on 2019-01-28
> **Autodave said:**
> What driver did you install for the Nvidia card and where did you get it from?

Generally, adding the *nomodeset* will allow you to get into the system until you get the correct driver installed.

You will always want to install the video driver from the repositories: never from the Nvidia site or any other site.

This is 100% true, and installing it from the repos will ascertain that it is **properly installed,** with all the dependencies, while the downloaded driver from nvidia.com will not.

---

