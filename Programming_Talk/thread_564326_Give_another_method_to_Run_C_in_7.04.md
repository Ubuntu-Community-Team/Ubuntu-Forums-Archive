---
title: "Give another method to Run C in 7.04"
date: 2007-10-01
forum: Programming Talk
---

### Post by mthalis on 2007-10-01
Is there any command without this 
      sudo aptitude install build-essential
to run C language in ubuntu 7.04.

---

### Post by eph1973 on 2007-10-01
You could use the Live CD you used to install with System>Administration>Synaptic Package Manager and get gcc off of the CD. (If for instance, you didn't have an Internet connection and were trying to build, say ndiswrapper).

---

### Post by mthalis on 2007-10-01
In my command work only ubuntu 7.04 live CD. but it didn't work 
after I install it also I don't have Internet connection.

---

### Post by dwhitney67 on 2007-10-01
I may be wrong, but it was my understanding that the build-essential packages are available on the Ubuntu CD.

Make sure you have this statement enabled in your /etc/apt/sources.list:

[FONT="Courier New"]deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted[/FONT]

---

### Post by eph1973 on 2007-10-01
If dwhitney's solution didn't work, you could try the following (with the CD in the drive):

```
sudo dpkg -i /media/cdrom0/pool/main/g/g*/*.deb
```

---

