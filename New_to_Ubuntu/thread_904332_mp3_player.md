---
title: "mp3 player"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by pomakkatu on 2008-08-29
i want to play mp3 music but its not working, am using ubuntu gutsy 7.10. somebody help me out

---

### Post by luckyuser on 2008-08-29
What exactly is not working? 
(Is your sound card not working? What media player are you using?)

---

### Post by ashmew2 on 2008-08-29
if you cant PLAY Mp3s or something , just visit this page :

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%207.10](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%207.10)

---

### Post by t0p on 2008-08-29
mp3 playback, and playback of many other proprietary format media, can be easily enabled by typing into terminal the command

```
sudo apt-get install ubuntu-restricted-extras
```

Agree "y" to all the other packages apt-get wants to install with this one.

---

### Post by tarvtarv on 2008-08-29
Hi, I have not been able to Install package can someone plz help:



sudo apt-get install libdvdread3
[sudo] password for User:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

Aslo when i try install mp3 codec it keeps saying to reload the list in a loop

I have ubuntu 7.1

---

### Post by kpkeerthi on 2008-08-29
Close all package managers - synaptic/apt-get/aptitude/add-remove programs. 
Got to System -> Admin -> Software sources and enable Universe and multiverse repositories and then try install the libdvdread package

---

### Post by tarvtarv on 2008-08-29
> **kpkeerthi said:**
> Close all package managers - synaptic/apt-get/aptitude/add-remove programs. 
Got to System -> Admin -> Software sources and enable Universe and multiverse repositories and then try install the libdvdread package
 
Manythanks bro.

---

