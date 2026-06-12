---
title: "Problem  with GeForce FX 5500"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by GoranI on 2008-08-14
I have UBUNTU 8.04 and graphic card nVidia GeForce FX 5500. After instaling ubuntu i can run only with max resolution of 800x600.I enabled restricted drivers for nVidia but after this resolution degraded on 640x... How can I solve this ???

---

### Post by LowSky on 2008-08-14
go to add/remove

look for nvidia-settings, it should pop right up with just nvidia

install

open a terminal type ```
sudo -i
```
leave the terminal open

go to system>admin> nvidia settings X or whatever

fix resolution and save X,, your G2G

---

### Post by hosk on 2008-08-14
I have one of those. If I remember correctly and nvidia-settings gives you no help, I needed to switch to the nvidia-glx-new drivers. Also sudo dpkg-reconfigure xserver-xorg. Worst case was editing my xorg.conf file.

---

### Post by xpod on 2008-08-14
Another here with the same card on another machine although mines always worked fine with the restricted drivers manager.

You could try rebooting into recovery mode and running xfix.

---

### Post by WRDN on 2008-08-14
I have the same card and had the same problem. You can find my solution [here]("http://ubuntuforums.org/showpost.php?p=5588265&postcount=2"), in your second of 3 threads on the same subject.

---

