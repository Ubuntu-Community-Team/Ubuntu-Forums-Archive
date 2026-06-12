---
title: "downloaded/installed ubuntu studio..."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by bm13084 on 2008-08-03
hi all,  i downloaded and installed the dvd of studio and installed it.  twice actually...  first time it let me choose a package and i did video.  came up as a black screen asking for user name and password, then gave me a terminal line.  second time,  i noticed a desktop option where it asked what packages to install,  so i picked that.  same end result.  now i'm stuck posting from my cell phone, cuz i wiped the unusable vista off...  is my dvd the problem?  am i picking the settings wrong?  any help is appreciated!

---

### Post by blue_shift on 2008-08-03
What hardware do you have?
Did you get any error messages in particular?

---

### Post by bm13084 on 2008-08-03
i have an acer 5720.  forgive me for not typing out all the specs on my phone.  the only error i get on start up is hal, which is network, which i can't install.  ubuntu hardy worked on here, but i don't have internet right now,  and i only downloaded the studio image.

---

### Post by blue_shift on 2008-08-03
I thought HAL was the hardware abstraction layer...

I'm going to post what I guess your specs are for other people, correct me if I'm wrong. 

2GHz Intel Core 2 Duo T7300; 1GB DDR2 RAM; 160GB hard drive; DVD-R/+R/-R DL/+R DL/-RW/+RW/-RAM; SD Card; 802.11 a/b/g/Bluetooth; 4x USB; 1x FireWire; PC Card; Express Card; 256MB ATI Mobility Radeon X2500;

Have you tried to start the X server from the command line? ```
startx
``` or better ```
sudo /etc/init.d/gdm start
```
Get any error messages?

---

### Post by bm13084 on 2008-08-03
actually, my problem is that i'm dumb.  i was using enter to select the packages instead of spacebar, which means i was installing nothing.  got it running. now off to install ndiswrapper!  thanks for your help though!

---

### Post by blue_shift on 2008-08-03
Unlucky! No worries, glad you got it sorted.

---

