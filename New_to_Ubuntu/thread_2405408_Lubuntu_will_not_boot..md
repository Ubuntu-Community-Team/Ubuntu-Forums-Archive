---
title: "Lubuntu will not boot."
date: 2018-11-05
forum: New to Ubuntu
---

### Post by earlysky on 2018-11-05
So I have a problem with Lubuntu. I installed Lubuntu on my internal hard drive (my hdd) and once it told me that it is finished downloading, it asked if I want to restart. So I restarted it. When it restarted the computer, it had a black screen with a _ blinking. I thought it was part of it booting up. (this was my first time installing Lubuntu)

It continued for hours, so I restarted the computer.. It did the same thing. So I put in the USB which I installed Lubuntu from onto my hard drive, and it loaded perfectly fine. No problems. But if I take out the USB and restarted my computer, it still does the blinking underscore. Any way to fix this??:confused:

---

### Post by wildmanne39 on 2018-11-05
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by Frogs Hair on 2018-11-05
Hello and welcome earlysky:   

Please post some information about your computer and tell us if you are dual booting with another operating system or installing Lubuntu on the entire disk.

---

### Post by earlysky on 2018-11-05
I have a Toshiba Satellite Laptop and I am installing on the entire disk.

---

### Post by earlysky on 2018-11-05
> **Frogs Hair said:**
> Hello and welcome earlysky:   

Please post some information about your computer and tell us if you are dual booting with another operating system or installing Lubuntu on the entire disk.
I have a Toshiba Satellite Laptop with 3gigs of ram and 256gigs of storage. I am trying to install Lubuntu on the entire disk.

---

### Post by yancek on 2018-11-06
If you selected the option on install to Erase Disk and install Lubuntu and did not change the default settings for Device for bootloader installation, it should have installed the system and bootloader properly.  Did you leave the default bootloader setting?  If you did and it still failed, you could try booting the Lubuntu install media again and go to the site below where you can download software called boot repair.  Read through the instructions on the page and select the 2nd option to download the ppa then run it using the option to Create BootInfo Summary and post the link you get when it finishes here.  Do NOT try to make any repairs.  THis will give members here enough information that they should be able to suggest possible solutions.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by valvegrid on 2018-11-07
I'm not sure if this helps, but I had exactly the same problem loading Lubuntu onto my 12 year old Toshiba NB-100, it loaded from the USB stick fine, but booting from the HD I got exactly the same results you were getting. 

What I found was happening during installation there is a box to ask if you want to update at the same time as installing. After many attempts I found by unticking the update box I could boot from the HD fine after that. After looking at the update list in Synaptic I notice the only significant update seemed to be the Kernel, rejecting the update cured the problem and updated everything else went fine leaving out the Kernel update. My old computer Definitely didn't like the new Kernel.

Keeping the original Kernel that came on the USB stick seemed to help, but I'm not sure of the security risk of doing this, but I wasn't too worried as I was planning on replacing the computer anyway because it was so old.

---

