---
title: "Intel GMA950 Driver &amp; Screen Resolution Issues"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by slowstuff on 2013-02-26
I have an older system that I decided to try Linux out on, this used to be my Windows Home Server.  It is a Foxconn 945G7MA Motherboard with Intel GMA950 graphics.  Ubuntu does not seem to detect the graphics and is limiting me to 1024x768.

I have tried several solutions, and while I have been able to get the screen resolution up where it should be the system still does not recognize the GMA950.

Things I have tried
[This]("http://ubuntuforums.org/showthread.php?t=1943652")
[This]("http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html")
[This ]("https://wiki.ubuntu.com/X/Config/Resolution")
[This]("http://ubuntuforums.org/showpost.php?p=11503588&postcount=4")
I have search here, and on Google, but keep running into dead ends & "Intel drivers are included in Ubuntu"...  The final thing I tried allowed me to at least set the resolution, but It would be nice if my "supported" video chip was detected.

Any help would be appreciated.
-Chris

---

### Post by PunkLV on 2013-02-26
```
sudo cat /etc/X11/xorg.conf
```
```
sudo cat /etc/default/linux-restricted-modules-common
```
Please post te output.

---

### Post by slowstuff on 2013-02-26
> **PunkLV said:**
> ```
sudo cat /etc/X11/xorg.conf
``````
sudo cat /etc/default/linux-restricted-modules-common
```Please post te output.

Both commands came back with "No such file or directory"

:EDIT: 
```
noah@Ark:~$ sudo cat /etc/X11/xorg.conf
[sudo] password for noah: 
cat: /etc/X11/xorg.conf: No such file or directory
noah@Ark:~$ sudo cat /etc/default/linux-restricted-modules-common
cat: /etc/default/linux-restricted-modules-common: No such file or directory
noah@Ark:~$ 
```

---

### Post by PunkLV on 2013-02-26
```
sudo nano /etc/apt/sources.list
```
Remove **#** from the lines beginning with '**# deb http://**
```
sudo apt-get update
apt-cache search intel | grep 950
```
Or any of the following keywords and their combination: xorg intel gma
In case you spot something similar to 'xserver-xorg-intel-restricted-drivers':
```
sudo apt-get install <that package name>
```

---

### Post by slowstuff on 2013-02-26
I followed those steps and installed xserver-xorg-video-intel and xserver-xorg-video-intel-lts-quantal.

Still said unknown under graphics, and still wouldn't let me set the resolution higher than 1024.  I decided to try restarting and once it hit what should be the Ubuntu loading screen it just sits and does nothing, tried restarting several times, it just sits there doing nothing now... :(

---

### Post by L3e68BF on 2013-08-10
i-m having the same problem here. No one can help us ...

---

### Post by deliomblj on 2014-03-12
Having the exact same issue here.
I followed the proposed guide. But i ended on the same dead end as everyone else..
I've been googling arround and is there a better place to post these kind of questions?

---

