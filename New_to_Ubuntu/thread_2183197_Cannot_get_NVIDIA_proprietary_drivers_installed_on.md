---
title: "Cannot get NVIDIA proprietary drivers installed on 13.1"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by xzDndye on 2013-10-23
Hi,

First time trying out Linux since 2004. I'm having pretty much the same issue as I did back then as well, I can't get the display driver to install.

I first tried 12.4 and read about all the issues it has with NVIDIA and so I downloaded the new version (13.1) on a disc and did a complete reinstall. 
My GPU is a GTX 670.

I've tried just about everything I could google, and after reinstalling the headers, image, and desktop, (many times) as well as going from lightdm to gdm, in addition to a bazillion ways of trying to install the driver (manual install from .run file from NVIDIA's website, installing from within the GUI, using various repositories), I seem to be down to these fundamental issues.

If I go into Software & Updates>Additional Drivers, it sees the NVIDIA drivers 304 & 319 as well as the Nouveau driver (which currenly is the only driver that is allowing me to boot to the GUI). 

If I do this and reboot, it takes me straight to a tty console on gdm. On lightdm it takes me to a low graphics mode which is equally as inescapable as the tty console. 

The only way to rectify the issue is to:> sudo apt-get remove --purge nvidia-*

Then, after rebooting or restarting whatever display manager service I'm using, I am back to the login screen and the nouveau driver is active again.

If I install the nvidia drivers from within the GUI (either via terminal or Software & Updates) and stay there, and try to load Steam I get this error message: > OpenGL GLX context is not using direct rendering, which may cause performance problems.

And if I go to the NVIDIA X server settings, it will say: > 
    You do not appear to using the NVIDIA X driver.  Please edit your X  configuration file (just run 'nvidia-xconfig' as root), and restart the  X server.

I am at a complete loss with this issue and I would really like to stick with Ubuntu but at this point I've been fiddling with it for over 6 hours and I'm about to try a different distro.

---

### Post by pqwoerituytrueiwoq on 2013-10-23
on a clean install of 13.10 run this in a terminal/tty
```
sudo apt-get install nvidia-settings-319-updates nvidia-319-updates -y
```
it is asking you to open a terminal and run ```
sudo nvidia-xconfig
``` then logout and in

---

### Post by xzDndye on 2013-10-24
Unforunately that brought me briefly to a tty console and then my monitor was blank.

I also tried another fresh install and did all this in order:
> sudo su
apt-get update
apt-get install linux-headers-generic
apt-get dist-upgrade
reboot
sudo su
apt-get install nvidia-current-updates
nvidia-xconfig
reboot

This had the same result as earlier and I had to uninstall the nvidia driver to get back to the GUI.

Really at a loss here.

---

### Post by pqwoerituytrueiwoq on 2013-10-24
i wonder if your monitor needs a edid hack to get it to work right, have a alternate monitor/tv?

---

### Post by xzDndye on 2013-10-24
Just to try it, I removed everything and reinstalled with Mint and did these steps again:

> sudo su
apt-get update
apt-get install linux-headers-generic
apt-get dist-upgrade
reboot
sudo su
apt-get install nvidia-current-updates
nvidia-xconfig
reboot

And I ended up being put back in a tty console which quickly transitioned into a blank screen with my monitor's green LED flashing.

Again, I could only get out of it by going back into tty and removing the NVIDIA drivers. After a reboot all is fine.

So at this point it's got to be a hardware issue on my end right? I'm not sure what an edid hack is but I will list my system:

CPU: Sandy Bridge i5 2500k (LGA 1155 & Z68 chipset)
GPU: Galaxy GTX 670 2GB
MEM: 16GB Corsair DDR3 1600 MHz
HDD: 120GB Corsair Force GT SSD
MB: Asus Maximus IV Gene-Z 
DVD: Asus DVD+/-RW 
PSU: Seasonic X750 Modular 750W

Also, my monitor is one of those 2560x1440 Korean IPS', a Yamakasi Catleap Q270 I believe.

Are there any BIOS settings I need to have?

By the way, thanks a lot for your help. And yes I have access to a 1920x1080 monitor if need be.

---

### Post by pqwoerituytrueiwoq on 2013-10-24
i would try it on that 1080p screen just to see if it will give you a display, for the sake of troubleshooting
you can also try the xorg edgers ppa and the beta nvidia driver
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y; sudo apt-get update
sudo apt-get dist-upgrade && sudo apt-get install nvidia-settings-331 nvidia-331 -y
```
to get rid of it do this
```
sudo apt-get install ppa-purge -y
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by xzDndye on 2013-10-24
You are a genius. Swapped in the 1080p monitor and got a clean 13.1 install and did the whole deal with the headers/drivers, restarted and it SEEMS to be working. Typing > sudo /sbin/lsmod | grep nvidia

Seems to indicate the driver is loaded. I'll test and make sure and report back. Do you have any ideas how to get the 1440p monitor working?

---

### Post by pqwoerituytrueiwoq on 2013-10-24
now that we know it is working i would plug it in and see if it works
if it does not work the issue is a firmware bug on the monitor/tv
HDMI has some DRM crap in it, the open source drivers don't give a crap about that and ignore that stuff (DRM = bad)
but the screen is sending bad info to the driver and the DRM complaint driver then turns the display off to prevent unauthorized copying
some times a edid hack can bypass this issue, only edid mod i have done was making the system treat the HDMI like a DVI port so i can use analog audio (HDMI audio is not worth the time, just a PITA)
if you want to be sure the drive is working run heaven/valley benchmarks on the system, if it runs showing the pretty scenery you are using the nvidia driver

edid stuff that may help you
[http://analogbit.com/node/23](http://analogbit.com/node/23)
what i did with mine:
[http://ubuntuforums.org/showthread.php?t=1926721&page=2&p=11712722&viewfull=1#post11712722](http://ubuntuforums.org/showthread.php?t=1926721&page=2&p=11712722&viewfull=1#post11712722)

i am sure a powerhouse card like a GTX 670 can run both screens at the same time

---

