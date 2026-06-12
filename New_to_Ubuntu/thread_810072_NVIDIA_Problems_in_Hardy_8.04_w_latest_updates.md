---
title: "NVIDIA Problems in Hardy 8.04 w/ latest updates"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nugznmugz on 2008-05-27
I cannot get my **Geforce 7800GS** to work properly.  

Without the **glx-nvidia-new** driver installed I get the proper screen resolution of 1280x1024.  **nvidia-settings** does not allow me to change any settings successfully.   

I do not get the proper refresh rate of 75hz with or without the driver.  The refresh rate is incorrectly reported as 73hz but my monitor is reporting 60hz.

Does anybodies nvidia card work with the latest drivers and updates?

Is there some information I can supply that might make my problem more obvious?  I have tried a lot of stuff mentioned in the forums so far and all of those things have resulted in failure and me reinstalling Ubuntu at least ten times due to my inability to undo those changes.

I was under the impression that installing video drivers and using compiz was relatively painless in Ubuntu but unfortunately out of the four different computers I have installed it on only one has been easy.  That one had a Intel 945 chipset.  My iBook G4 won't even display after loading the kernel.  My Presario M300 is too old to support any of the extra graphics.

I really want to use this operating system but I just can't do it at 640x480@60Hz.

Thanks for any help,
NNM

---

### Post by webaake on 2008-05-28
You need the Nvidia 173.08 BETA drivers.
Link with download and install instructions:

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

Works very well with my 8.04 and 7600GS. A bit tricky to install and needs to be installed after every kernel upgrade, but worth the effort!

Good luck!

---

### Post by Crafty Kisses on 2008-05-28
> **webaake said:**
> You need the Nvidia 173.08 BETA drivers.
Link with download and install instructions:

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

Works very well with my 8.04 and 7600GS. A bit tricky to install and needs to be installed after every kernel upgrade, but worth the effort!

Good luck!

Yeah, the update actually solved almost all of my issues.

---

### Post by Delever on 2008-05-28
Tested guide to get it working after kernel update (save it somewhere):

1. Rename your downloaded file which ends with .run to nvidia.run and place to your home directory (i.e. /home/you)

2. Install libraries for compiling things:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

3. Reset xorg.conf to basic state (if you need some settings in xorg, make backup of it before running this):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Log out, Log in. Resolution may have changed.

5. Turn off Gnome Display Manager, this will send you to console.
```
sudo /etc/init.d/gdm stop
```

6. Log in there.

7. Run nvidia installer:
```
sudo sh nvidia.run
```

8. Follow instructions, let it modify xorg.conf when it asks.

9. Start GDM again:
```
sudo /etc/init.d/gdm start
```

---

