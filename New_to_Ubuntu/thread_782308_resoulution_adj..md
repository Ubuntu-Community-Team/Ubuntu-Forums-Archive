---
title: "resoulution adj."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by creekchub on 2008-05-04
hello i am a new convert just getting my feet wet in the linux world. i decided to try ubuntu and have it up and running on my new pc.  anyhow i cannot get my resoulution settings to go higher than 800x600.  i started the EnvyNG and downloaded the driver.  when i reboot and log on a screen box appears states resolution to hight and my screen goes black. i have to reboot in safe mode and reconfigure and reboot to normal.  what do i need to get my resolution up? my pc specs are in my signature

---

### Post by alienexplorers on 2008-05-04
Run sudo nvidia-settings to set your resolution.

---

### Post by Tatty on 2008-05-04
Try reconfiguring X with:

```
sudo dpkg-reconfigure xserver-xorg
```

Make sure you select the resolution you want to use when prompted.


If that fails try using envy to install an older driver. I have a Nvidia Geforce Go 6100 and the latest nvidia driver was causing me lots of problems with black screens so i used envy to install the 96.43.05 driver.

---

### Post by creekchub on 2008-05-04
ok how do i go about performing either of these tasks.  i am just getting my feet wet with this distro!!

---

### Post by doorknob60 on 2008-05-04
Just run the commands in the terminal (Applications->Accessories->Terminal). Also, I'd for sure try using the older driver with envy, because I've had problems on my Geforce go 6150 with the newer driver (though they seemed to disapear so far in Hardy...I think...I might still have the old driver :P). To install the older driver, choose manual install in Envy and choose the 96.x driver (I forgot the exact number of it).

---

### Post by alienexplorers on 2008-05-04
On my FX-5200 I also have to run the nvidia-glx driver since the nvidia-glx-new will not work.

---

### Post by creekchub on 2008-05-05
well tonight i was trying my hand at the commands above to no avail. i will figure this out thanks for all your help and support so far.  slowly but surely i will get it

---

### Post by creekchub on 2008-05-07
> **Tatty said:**
> Try reconfiguring X with:

```
sudo dpkg-reconfigure xserver-xorg
```

Make sure you select the resolution you want to use when prompted.


If that fails try using envy to install an older driver. I have a Nvidia Geforce Go 6100 and the latest nvidia driver was causing me lots of problems with black screens so i used envy to install the 96.43.05 driver.

well i tried the above to no avail will an onboard video have any effect?  anyhow here is what i get when i try to configure the xserver


You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by creekchub on 2008-05-10
well i do not know exactly how i did it but i finally got a 1024x700 resoulution and things are much beter

---

