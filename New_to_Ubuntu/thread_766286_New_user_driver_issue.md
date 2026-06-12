---
title: "New user driver issue"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ShatteredReality on 2008-04-25
Hi,

I am 100% new to Linux but feel its time to look into alternatives to windows. I successfully dual booted my machine so i have an Ubuntu and Vista partition. So far I have not had much trouble outside of drivers. Mainly my video driver. I am running a Nvidia GeForce 9600GT graphics card. I downloaded and install the beta driver off of the Nvidia website and it seemed to work but every time I restart the machine it says the card was not recognized and I end up reinstalling the driver every time I reboot. I hope there is an easy fix. any help is appreciated.  Thanks!

---

### Post by Saya on 2008-04-25
Try ```
sudo apt-get install nvidia-glx-new
``` in a terminal window.

---

### Post by ShatteredReality on 2008-04-25
Well i tried that and after a reboot it is once again not recognizeing the card. Also I attempted the reinstall the driver (somthing which has fixed the issue in the past) and that no longer seems to work. I should also mention that no 3rd party driver appear under the Hardware Drivers window.

---

### Post by starcannon on 2008-04-25
This is normally an easy issue, but since you've got a couple drivers plastered on each other lets start over, ( all I run is Nvidia here and My method works perfectly on my machines ) Print this out, were going to do some cli with no gui available to get this just right.

1st move the NVIDIA driver you downloaded for your card from [www.nvidia.com](www.nvidia.com) to your Desktop (if its not already there), then:
```
CTRL-ALT-F1
login
password
sudo /etc/init.d/gdm stop
cp /etc/X11/xorg.conf /home/yourhome/xorg.conf.bak
sudo rm /etc/X11/xorg.conf
cd /home/yourhome/Desktop
sudo chmod a+x ./NVIDIA*
sudo apt-get install build-essential
sudo ./NVIDIA*
sudo /etc/init.d/gdm start
```

Okay that should have your Nvidia driver installed, now we want to get it working on reboots so.
```
Alt-F2
gksudo gedit /etc/modules
```
Now add this to that file:
```
nvidia
```
save

Now make sure the old default driver doesn't load:
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

Make sure that your Disabled Modules has "nv" in it, something like this:
```
DISABLED_MODULES="nv"
```

Okay that should do it.
Let us know how you get on.

---

### Post by ShatteredReality on 2008-04-25
That seems to have fixed the issue! Thanks alot!

---

