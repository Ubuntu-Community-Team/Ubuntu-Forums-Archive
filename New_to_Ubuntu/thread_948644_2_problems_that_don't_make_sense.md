---
title: "2 problems that don't make sense"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by scooop08 on 2008-10-15
When I go to  aol to check my email my username and password don't show up.


Then when I got the flash website to download flash the download button never pops up even thought I tell it what type of Ubuntu I have

---

### Post by SpenceMakesSense on 2008-10-15
you can get flash from the repositories
i believe it is ```
 sudo apt-get install flashplugin-nonfree
```
Ill double check that though
if that doesnt work just try
```
 sudo apt-get install flash-nonfree
```
Ive seen both.

---

### Post by scooop08 on 2008-10-15
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Thats what was give

---

### Post by jamesrl on 2008-10-15
Add the following lines to /etc/apt/sources.list:
```

deb http://packages.medibuntu.org hardy free non-free
deb-src http://packages.medibuntu.org hardy free non-free

```
this was in response to "Package not found", ignore ... it seems you have flash installed.

---

### Post by scooop08 on 2008-10-15
So could it be something with java then?


Or is this in no relation to my email

---

### Post by Keen101 on 2008-10-15
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by scooop08 on 2008-10-15
Still when I go to youtube it tells me that either java is turned off or flash isn't installed


I still can't log into aol either

---

### Post by scooop08 on 2008-10-15
Sorry everyone I figured it out some how I downloaded and script blocker

---

