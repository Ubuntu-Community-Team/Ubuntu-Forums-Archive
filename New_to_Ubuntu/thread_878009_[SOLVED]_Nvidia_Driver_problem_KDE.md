---
title: "[SOLVED] Nvidia Driver problem KDE"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by peterjakey on 2008-08-02
Hi, I recently installed Kubuntu which is now dual booting with XP. I enabled the Nvidia restricted driver, now I cant change the screen res higher than 640x480 (even in Administrator mode), however all the compiz effects work like wobbly windows, cube etc. I tried downloading and installing the nvidia driver from nvidias site, this gave me the same problem. I have also tried using ENVYNG to install the nvidia driver but still I cant change the screen res. The card is Nvidia Geforce 7300 SE. Any help would be very much appreciated.

---

### Post by eightmillion on 2008-08-02
You'll probably just have to manually add your desired resolutions to your /etc/X11/xorg.conf
> kdesu kate /etc/X11/xorg.conf
Find this section:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

```
Add your desired resolution on the modes line. For example:
```

                Modes           "1920x1200" "1280x800"

```
Then save the file and log out and log back in.

---

### Post by peterjakey on 2008-08-02
Thanks, but Im still having the same problem, also when I install the video driver X server fails to load on reboot, i get the error message

kinit : NO resume image, doing normal boot...

This only allows me to use the console, so to solve this I have to boot into recovery mode and repair X server which changes everything including the .conf file I added the screen res setting to

---

### Post by eightmillion on 2008-08-02
> kinit : NO resume image, doing normal boot...
This message is completely normal. It has to do with coming back from hibernation.

Have you tried nvidia-settings ?

> sudo apt-get install nvidia-settings

It's pretty handy for setting up nvidia cards.

---

### Post by peterjakey on 2008-08-04
I have just bought a new monitor and it now works perfectly with the restricted driver =D

---

