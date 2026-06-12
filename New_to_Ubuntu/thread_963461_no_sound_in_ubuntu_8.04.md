---
title: "no sound in ubuntu 8.04"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by kanhiya on 2008-10-30
:mad::(:confused::(hello everybody i am unable to hear sound while playing music infact song was playing there and i played same song in windows finely i also checked volume level all are high whether it is of system or from totem movie player i also tried to play same and also other songs using rythembox music player guys i am using linux first time please help me

---

### Post by northern lights on 2008-10-30
Can you please post the outputs of ```
sudo lshw -C multimedia
```and```
cat /proc/asound/cards
``` Thank you.

---

### Post by nagaraja on 2008-10-30
Check whether mp3 codec has installed in ur system or else type

sudo apt-get install w32codecs

---

### Post by kanhiya on 2008-10-30
> **kanhiya said:**
> :mad::(:confused::(hello everybody i am unable to hear sound while playing music infact song was playing there and i played same song in windows finely i also checked volume level all are high whether it is of system or from totem movie player i also tried to play same and also other songs using rythembox music player guys i am using linux first time please help me
my output is                                                               [sudo] password for kanhiya: 
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
                      HDA SIS966 at 0xfd5f0000 irq

---

### Post by kanhiya on 2008-10-30
> **nagaraja said:**
> Check whether mp3 codec has installed in ur system or else type

sudo apt-get install w32codecs

i got this output 
kanhiya@kanhiya-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by kanhiya on 2008-10-30
my output is
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
0 [SIS966 ]: HDA-Intel - HDA SIS966
HDA SIS966 at 0xfd5f0000 irq

---

