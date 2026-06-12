---
title: "[SOLVED] hardy heron and compiz/beryl/compiz-fusion"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by BlackKnight7891 on 2008-05-29
im trying out hardy heron in an attempt to leave windows vista and microsoft in the dust.

atm im trying to get the cool eye candy features working with hardy.
been reading as much stuff as i can find on it but im still not sure of whats going on could someone please confirm the following

ubuntu 8.04 has compiz preinstalled and simply needs to be turned on /configured. 

if it is do i need add on's to get things like flaming windows and the 3d cube. 

if not how do i install it on hardy?

Discovery of the day:: nothing kills starcraft not even vista ultimate or Linux. game developers take a close look.

---

### Post by Kingsley on 2008-05-29
Desktop effects automatically turn on after you install 3d drivers in Hardy.

---

### Post by forestpixie on 2008-05-29
You need to specify custom in the appearances - visual effects menu and install the settings manager.

Run this in a terminal to install it
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by bumanie on 2008-05-29
> sudo apt-get install compizconfig-settings-manager
To set up follow this guide [http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by BlackKnight7891 on 2008-05-29
Fantastic, i have the latest nvidia drivers for my 8800gt and the "extra graphics" turned on under apperance, will try that guide tonight

---

### Post by forestpixie on 2008-05-29
>  the "extra graphics" turned on under apperance

You need to turn on custom - if you don't have a custom option and drivers are installed properly you wioll need to install simple-ccsm

```
sudo apt-get install simple-ccsm
```

---

### Post by BlackKnight7891 on 2008-05-29
its all good got it working

---

