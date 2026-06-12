---
title: "Atom N270 + GMA950 + Ubuntu 12.04 = Lag?"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Cryonics on 2012-06-26
man, I'm having hard time using ubuntu on my N270 atom powered BENQ JoyBook Lite U101! 

this baby can even run windows 7 at tolerable speed, but ubuntu is lag like hell that can make me crush my netbook.

opening application is pain in the a*s, takes up to 10 seconds to only open firefox, lags while scrolling pages

is it driver issue? my chipset is 945GM and Intel GMA950 graphic,
please help or else I need to remove my ubuntu which is sad

---

### Post by Cryonics on 2012-06-27
bump

---

### Post by Carborundum on 2012-06-27
I have an Asus EeePC 901 with that CPU and chipset. It runs Ubuntu 12.04 smoothly. It's hard to say exactly why your machine doesn't without more information.

How much memory do you have? You need at least 1 GB if you want to use Unity, otherwise you can try switching to a lighter DE with a smaller memory footprint, like XFCE or LXDE.

Open a terminal and write 'top' to see which processes are using the most memory and CPU-time. Press 'Shift+P' to sort by %CPU and 'Shift+M' to sort by %MEM.

---

### Post by black veils on 2012-07-01
you could try the distro Xubuntu, but if that is still too slow, you could have Lubuntu or Bodhi Linux. Xubuntu has many features, and can be rearranged like the old gnome, but is lighter on resources.

to test the xfce desktop which Xubuntu uses, you can install it on your current system, and choose the Xubuntu (xfce) desktop at login screen.

```
sudo apt-get install xubuntu-desktop
```Edit:

i just looked at the specs for that model, 512ram is not enough for Ubuntu to run smoothly. the above info will be useful!

**also, once you settle on a system, you may want to do this:**

open the Terminal and copy-paste the following
```
gksudo gedit /etc/sysctl.conf
```press Enter.

scroll to the bottom of the text file and add your swappiness parameter to override the default, so copy-paste the following lines
```
#
# Decrease swap usage to a workable level
vm.swappiness=10
```close the text file and reboot your computer.

After the reboot, check the new swappiness value:
open the Terminal and copy-paste
```
cat /proc/sys/vm/swappiness
```Press Enter.

Now it should be 10.

---

### Post by I2k4 on 2012-07-01
Similar Acer netbook here - runs W7 slower than I like - after a lot of Ubuntu version testing on Live USB I found everything _after_ Ubuntu 10 / Mint 11 was just too slow.  I decided for the couple years' remainder of this machine's life it will be Lubuntu 10.10 (runs like stink, but support and software updates have ended - fine with me).  

As far as I can see, Ubuntu is going through its "Vista phase" simply leaving low powered machinery behind as Windows did the XP hardware.  Personally, I wouldn't use Ubuntu 12 / Mint 13 in a machine that doesn't run W7 satisfactorily.

---

### Post by exeuntfor on 2012-08-25
use lxde, better for you

sudo apt-get install lxde, then select first screen.


then install xorg-edgers driver for gma950, last thing use chrome, less xorg uses then firefox

---

