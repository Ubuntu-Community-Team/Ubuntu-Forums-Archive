---
title: "Audio humm on 24.10"
date: 2024-11-15
forum: New to Ubuntu
---

### Post by brettwstevens69 on 2024-11-15
Hi community, This is my first time posting on any forum so please excuse the non etiquette if there is any.
I've been a long time Nix user (1983) and have used Ubuntu for the past 14 years. I'm a retired systems admin but am having an audio issue that's got me stumped.
I've got a P50 Lenovo Thinkpad that I use for my daily computing running 22.04. It's a bit long in the tooth like me 7-8 years old.
It's got a Nvidia discreet graphics card and an i7 6820cpu.
The audio device listed through lspci -v is 
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
and speakers are connected through the headphone jack.
I've booted the USB with Ubuntu 24.10 and as soon as the distro starts to load I get a pop and a loud hum through the speakers that continues even when the desktop loads.
If I use my volume up or down buttons the hum goes away or if any audio is played the hum goes away. But as soon as there is nothing going on it hums again.
It doesn't happen on older distros just 24.10 based one's. 
Was wondering if anyone has had this problem with older hardware or could it be an updated pipewire bug or driver error or maybe my hardware is just to old now.
The kernel driver is snd_hda_intel 
Thanks for your time.

---

### Post by outofcheese on 2024-11-17
I remember having seen a similar issue on a laptop (a thinkpad as well) 5-6 years ago, it turned out to be a problem with the power save mode of the card. I'm not saying I'm 100% sure that's what's happening on your machine but it could be an angle to attack the problem.
First, confirm power save is turned on
```
cat /sys/module/snd_hda_intel/parameters/power_save
```
"1" means it's on.
Then if you
```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save 
```
and the hum stops, that means bingo we won.
To make it permanent back then we put a config file in /etc/modprobe.d/ containing
 ```
options snd_hda_intel power_save=0
```
I don't know if this is the "modern" version to do things the right way, I changed my profession since ;)

---

