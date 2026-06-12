---
title: "No hardware acceleration with nvidia-current"
date: 2011-05-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-05-14
I wanted to try out the acceleration video mode from Adobe Flash 10.2. libvdpau1 ist installed and in /etc/adobe/mms.cfg EnableLinuxHWVideoDecode is set to 1.

But if I watch an example video I get "software video rendering". I uninstalled nvidia-current and tried the drivers from nvidia.com. The installation was successfull and a xorg.conf was created but after a reboot the desktop environment haven't started. I don't know if I need something other to configure because this was my first manual installation.

I reinstalled nvidia-current and rebooted the system. Now I got on the example flash video "accelerated video mode" and the performance increased heavily. I figured out this was because the manual installed nvidia drivers wasn't uninstalled. After I uninstalled them and rebooted the system I had again "software video rendering".

The xorg.conf from nvidia-current and the official nvidia driver was the same except that the official driver had the NoLogo entry set to true so the xorg.conf isn't the problem.


The question is how can I activate hardware acceleration on nvidia-current? Or is this only possible with the official nvidia drivers?

I'm using Ubuntu 11.10 dev and the version of nvidia-current in the repository is currently 270.41.06 (the same which is currently on the nvidia site).

---

### Post by Sworddragon on 2011-05-15
I figured out that the official NVIDIA driver needs at least /usr/lib32/vdpau/libvdpau_nvidia.so.270.41.06 to use the hardware acceleration. Removing this file will cause it to not work. I backup this file and copied it back if only nvidia-current was installed but it hasn't work in this case. nvidia-current has even his own file at /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.270.41.06.

---

### Post by The Cog on 2011-05-15
Moved to Ubuntu+1 as requested by the author.

---

### Post by Sworddragon on 2011-05-18
I found now a solution. The command
```
sudo ln -s /usr/lib32/nvidia-current/vdpau/libvdpau.so.270.41.06 /usr/lib32/libvdpau.so
```
is just needed. libvdpau1 isn't needed then anymore.

---

