---
title: "Hardware device list"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by jamere on 2008-06-07
Hi all,

Is there a way to get a detailed hardware device configuration of my pc using "terminal" or otherwise? Need specifically to find sound card info but would like to see other device info also. Thanks much...jim m

Note: did a recent partial upgrade of Hardy Heron 8.04 (kernel 2.6,24-18 ) that was offered by Update Mgr and lost all sound functions. Hope fixes come soon through the Update Mgr channels!

---

### Post by Rocket2DMn on 2008-06-07
You can view a detailed hardware list by running
```
sudo lshw
```
Specifically for sound, you can run
```
sudo lshw -C sound
```
and
```
lspci | grep audio
```

---

### Post by chika.tambun on 2009-05-02
$ sudo lshw -short
[of course it leaves a lot of about the detail behind, but make it easier]

$ sudo apt-get install lshw-gtk
$ sudo lshw-gtk
[user-friendly GUI, more intuitive]

---

