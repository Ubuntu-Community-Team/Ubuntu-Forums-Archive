---
title: "alsa problem?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by DMinard on 2008-05-13
this problem stems from the fact that i want to run WOW through wine but i have no sound. i checked my sound setup and i  found i cant run my alsaconf  seems it doesnt exist?  i tried to then run sudo apt-get install alsa and it says im up to date. if im up to date how do i set up my alsa? the previous distribution of linux i tried the alsa sound ran great once i was able to configure it, perhaps this is the same im just too new to know i suppose.  anyone able to help?

---

### Post by encompass on 2008-05-13
You could try winecfg.... this program has a sound setting system.  If you haven't setup sound for alsa there then you probably won't get sound at all.
Hope this helps.

---

### Post by zenwalker on 2008-05-13
Seems the driver isnt got loaded up. 

Check if the device has been detected using lspci cmd. If its detected, then issue modprobe | grep sound cmd to see if the driver has been loaded. If not, then u can insmod sound modules to the kernel,provided if u know the path of where sound drivers are present.

---

### Post by Xiong Chiamiov on 2008-05-13
I have found that sound through Wine tends to have problems for me.  That said, I listen to my Guild Wars soundtrack through amarok while I'm playing, so I've no complaints.  And yes, try playing around with the audio tab in Wine configuration.

---

