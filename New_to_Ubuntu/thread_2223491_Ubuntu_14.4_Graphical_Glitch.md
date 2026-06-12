---
title: "Ubuntu 14.4 Graphical Glitch"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Pikboom on 2014-05-11
Whenever I try to access a web browser like Google Chrome or Firefox, Everything on the screen goes buggy, with garbled text and some strange buggy graphic in the upper right hand corner. I don't know what could be causing this, but I'm trying to get a screenshot of it.

---

### Post by Vladlenin5000 on 2014-05-11
Hi, welcome.
Please do that, post a screenshot. Also tell us your system specs, namely the graphics card and whether or not you're using proprietary drivers for that piece of hardware.

---

### Post by Pikboom on 2014-05-11
The graphics card I am using is the ASUS Geforce GTX 660 DirectCU II OC. I am using the drivers that came with it. Also, my computer was working fine until I upgraded from Ubuntu 13 to 14.04. Still trying to get a screen shot, The computer freezes after I do sometimes :\

---

### Post by Vladlenin5000 on 2014-05-11
> **Pikboom said:**
> I am using the drivers that came with it.

What are those drivers exactly? Graphics cards usually AREN'T shipped with Linux drivers... If you just installed Ubuntu and didn't select any option in "additional drivers" then you're using the open-source driver which is limited and probably not even recommended for newer chips like the GT660. 

Please go to System Settings > Software & Updates; select the last tab "additional drivers", wait a few seconds (up to a couple of minutes) and the system should present you the options for nVidia's proprietary drivers, along with the aforementioned open-source driver (codename 'nouveau') that should be the one currently in use. Then select the recommended proprietary driver version, wait for the download & install, reboot and test again.

---

### Post by Pikboom on 2014-05-11
Here is a link to the screenshot:
[https://drive.google.com/file/d/0B28z0HPgJfNHMDJvaUdkTkJ1OTg/edit?usp=sharing](https://drive.google.com/file/d/0B28z0HPgJfNHMDJvaUdkTkJ1OTg/edit?usp=sharing)

---

### Post by Vladlenin5000 on 2014-05-11
Yeap, you need proper drivers. Please try the procedure I mentioned earlier.

---

### Post by Pikboom on 2014-05-11
It works! Thanks a bunch!

---

### Post by Vladlenin5000 on 2014-05-11
You're welcome. Anything else you need please post and we'll try to help you.

Now you have a proper setup to enjoy resources demanding games. The GT660 (with nVidia's drivers) should be powerful enough to handle anything you want to try.

PS - Please use the thread tools to mark this thread as solved. Thank you.

---

