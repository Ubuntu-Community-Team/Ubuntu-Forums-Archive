---
title: "System randomly and repeatedly falls asleep"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by schreiberbj on 2012-07-08
I am running ubuntu 12.04 on an old laptop. I am fairly new to linux, and don't really know how to troubleshoot it. I have noticed an unusual problem several times over the last few weeks. 

I will use my computer normally for a while, but then it will start falling asleep randomly. At least, I think it is falling asleep. The screen goes dark, but fades back in when I touch the trackpad. Even after I wake it up, it continues to fall asleep every few seconds until I restart the computer. I think it happens after I switch from one of the virtual consoles back to the graphical environment, but I am not sure. 

Any help with either fixing this or tracking down the problem would be appreciated.

---

### Post by AlbertJB on 2012-07-08
To begin with, you could specify the laptop model, GRAPHICAL CARD,  etc...

---

### Post by schreiberbj on 2012-07-08
It is an hp Compaq nc4200. Intel Pentium M 1.86 GHz processor. 1.5 GB of ram.

---

### Post by AlbertJB on 2012-07-08
So maybe the problem is the graphical card: Intel Graphics Media Accelerator 900, up to 128-MB shared system memory (from what I've searched in HP web). The driver you have installed is the i915 ? I've found this: [http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus](http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus) Hope givves you some hints.. You can do an X-diagnose and put the output here...

---

