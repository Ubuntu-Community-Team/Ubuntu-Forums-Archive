---
title: "I think i am using on board graphics instead of my RX 480. 10 FPS. HELP"
date: 2017-01-10
forum: New to Ubuntu
---

### Post by 2kew on 2017-01-10
Ok, i am a linux noob. Just started yesterday. Installed Ubuntu from  USB. Tried the AMDGPU-PRO drivers and was getting crashes. Read up on  how the mesa drivers might be better so i tried to get those. I used the  Podoka PPA and did Sudo apt-get update and Sudo apt-get upgrade.
  When i run CS GO i get no more than 9 fps. I have a RX 480 on windows i get 300+ so i think something is wrong. 

lspci -k | grep -EA2 'VGA|Display' gives me
```


00:02.0 Display controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
Subsystem: ASRock Incorporation Motherboard
Kernel driver in use: i915

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67df (rev c7)
Subsystem: XFX Pine Group Inc. Device 9480
Kernel driver in use: amdgpu
```

---

### Post by alexeyn on 2017-01-11
make /etc/modprobe.d/c.conf
and add 
blacklist i915
to it

---

