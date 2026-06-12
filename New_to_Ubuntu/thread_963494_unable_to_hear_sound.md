---
title: "unable to hear sound"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by kanhiya on 2008-10-30
i have done following in checked all the volume and try different players song was playing but no voice was there and i played that song in windows finely  and below is the outputs of terminal                kanhiya@kanhiya-laptop:~$ sudo lshw -C multimedia
[sudo] password for kanhiya: 
Sorry, try again.
[sudo] password for kanhiya: 
  *-multimedia            
       description: Audio device
       product: Azalia Audio Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52 module=snd_hda_intel
kanhiya@kanhiya-laptop:~$ cat /proc/asound/cards
 0 [SIS966         ]: HDA-Intel - HDA SIS966
                      HDA SIS966 at 0xfd5f0000 irq 19
kanhiya@kanhiya-laptop:~$ 
kanhiya@kanhiya-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
kanhiya@kanhiya-laptop:~$

---

### Post by eternalnewbee on 2008-10-30
Take a look at this Thread:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
EDIT: Go to: Main Menu > System > Administration > Software Sources, and enable Software restricted by copyright or legal issues. Then try to install the w32codecs again.

---

