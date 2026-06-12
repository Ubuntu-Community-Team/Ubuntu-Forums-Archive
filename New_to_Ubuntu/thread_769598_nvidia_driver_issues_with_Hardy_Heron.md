---
title: "nvidia driver issues with Hardy Heron"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by GeneticFlea on 2008-04-26
Ive upgraded to Hardy Heron and im having issues with Nvidia drivers. Ive got a thinkpad t61p with a nvidia quadro 570m, and im currently having to use the generic drivers. Under restricted drivers, it displays the nvidia option, but when i check enable, it just greys out for a second and then tells me i need to restart, while never checking the box. On restart it still only uses the generic drivers. Oddly, under screens and graphics if i click the drivers tab, it lists the nvidia driver as being used, but i cannot get any of the correct resolutions nor can I use any graphical features and the colors are not true 32bit.

Any help? Should i just reinstall? if it matters im using 64bit.

---

### Post by SOULRiDER on 2008-04-27
Try running
```
sudo nvidia-xconfig
```
Lets see if that helps you with the drivers.

---

### Post by GeneticFlea on 2008-04-27
It says "command not found"

---

### Post by SOULRiDER on 2008-05-09
Install the drivers then:
```
sudo aptitude install nvidia-glx
```

---

### Post by Xiong Chiamiov on 2008-05-09
You can also try installing the driver directly from NVIDIA.  Download it from their site, then go to a prompt (ctrl+alt+f2) and run
```

sudo /etc/init.d/gdm stop
cd [wherever you put the installer]
sudo ./NVIDIA-[tab]
startx

```

---

