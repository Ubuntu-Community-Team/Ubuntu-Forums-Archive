---
title: "Cannot boot after fresh install, 10.04"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by LinuxNubie on 2012-09-05
Hello,

I recently installed 10.04 LTS. I was able to boot from LiveCD. Hwoever after installation, I get post boot beeps and then a blank screen. I suspect it is a video driver issue. Can someone please tell me how I can resolve this ?

I have an ATI HD3450 card DVI/VGA

Thanks,

---

### Post by oldos2er on 2012-09-05
Post moved to its own thread.

---

### Post by ajeannotte on 2012-09-21
same issue. i haven't been able to figure it out, but have made progress muching around within the guts of grub. i can at least now get a command line by pressing cntl + alt + (F1-F6) but have no idea what to fix to get it working. i've put off upgrading linux because of this for the last 2 years.

- live CD boot, no graphics problems at all. 
- after install, no graphics at all. cannot see grub.

i tried installing a few different ways with no result. last try was wiping the whole drive, new partition table, swap sda1, home sda2, root sda3 (with room to install other operating systems IF i get this one working)

nVidia 7900GT graphics card. no issues yesterday. upgrade, not working.

---

### Post by Bashing-om on 2012-09-21
Here is one option; Try and see.

Boot to command line video issues:
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
```
sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current
``````
sudo apt-get purge nvidia-common
```#Install nouveau and remove the xorg.conf
```
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```[INDENT][INDENT]hth <==BDQ
[/INDENT][/INDENT]

---

