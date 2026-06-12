---
title: "Kubuntu stuck with black screen"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by korbes on 2016-09-09
Hi,
I did a fresh install of kubuntu 16.04. At first everything worked fine. But unfortunately after a reboot of my system kubuntu won't load. It gets till the kubuntu splash screen with the blue loading bar. And after that I get a black screen. Even not a mouse pointer. The only thing that I can do then is to hard reset my pc.
I have a dualboot with win10. And win10 loads fine.
Any help? Thanks in advance.

---

### Post by mastablasta on 2016-09-09
first we'll need a bit more informaiton on the system: [SIZE=2]https://ubuntuforums.org/showthread.php?t=1422475
[/SIZE]
is the graphics intel/nVidia maybe?

you could also try one of the boot options:
[SIZE=2]https://help.ubuntu.com/community/BootOptions
[/SIZE]

finally you should have the option to boot into recovery and check the logs or troubleshoot from there: 
[SIZE=2]https://wiki.ubuntu.com/RecoveryMode
[/SIZE]

---

### Post by korbes on 2016-09-09
Yes I have a radeon r7 240 card. And i think its the driver that causes problems . I booted kubuntu in recovery mode and selected the top option that sais: continue booting. Then kubuntu starts but with lousy graphics. But I cant manage to install the right driver. I followed 2 different tuts on ask.ubuntu but still no luck.

---

### Post by korbes on 2016-09-09
I followed this tut: [http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics)
still no good. I can only start in recovery mode.

---

### Post by mastablasta on 2016-09-09
ok so you are using opensource *radeon* driver since AMD dropped support for this chip in the new version of Ubuntu. 

have a look if there is anything here that can be helpful: [SIZE=2]https://help.ubuntu.com/community/RadeonDriver

if you have Intel GPU added in the mix then look here for answers (maybe osmething needs to be enabled for GPU switching): 
[SIZE=2]https://help.ubuntu.com/community/HybridGraphics


[/SIZE]another option is to use an older version of Ubuntu (at least for now). 14.04 and 14.04.1 should work i believe (you would get fglrx support which is the closed soruce driver from AMD) and this version is then supported until 2019. hopefully the issue you have (if it's not hybrid GPU) will be resolved in radeon driver by then.
Option 2 is to load a newer radeon driver (e.g. beta) and the issue might be resolved.

still i find it strange the chip is not working well. hopefully the install was well done and you didn't attempt some manual AMD driver instalation.



[/SIZE]

---

