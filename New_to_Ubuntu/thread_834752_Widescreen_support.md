---
title: "Widescreen support"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by biehlbuddy on 2008-06-19
I'm sure I'm not the only one with this problem so I figured it would make a good first post.  I am having trouble configuring my resolution and am stuck at 800x600 and cant go any higher.  My video card is a GeForce FX 5200 and I would like to set my resolution to 1440x900, or anything wide screen really.  Any help would be great.

---

### Post by Delever on 2008-06-19
It seems that you probably don't have nvidia drivers installed. Do you have any choices in System->Administration->Hardware Drivers?

---

### Post by wpshooter on 2008-06-19
I had a similar but I don't think exactly the same problem with trying to get a wide screen Samsung monitor to configure recently and what I found out was that the Y-RES parameter in the usplash configuration file was being configured by the operating system installation as 1440 instead of 900.  Once I manually changed that parameter in the usplash configuration file and then applied it by running some "I think" dkgp or something like that command that I found in another thread and then rebooted, then the 1440 x 900 resolution was on the system/preferences/resoltuion listing and all I had to do was choose it.

Good luck.

---

### Post by Delever on 2008-06-19
Ok, here are things which I would do:

Reconfigure x server for high settings:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Log out, log in.

If video acceleration does not work, install envyng:

```
sudo apt-get install envyng-gtk
```

Go to Applications>SystemTools, run EnvyNG, let it download and install NVIDIA drivers.

---

### Post by biehlbuddy on 2008-06-19
I have all the current drivers installed, I heard I could edit the xorg.conf file and type in the resolution I want where it says "modes" and then type in "1440x900" attached is my xorg.conf and I have no Idea where to put it:

While using 6.04 I was able to set up dual monitors and everything with a fairly high resolution, now with 8.04 the highest I can get is 800x600.  :confused:

---

### Post by dicecca112 on 2008-06-19
if you indeed have the nvidia drivers installed, install nvidia-settings

```
sudo apt-get install nvidia-settings
```

and then run it as sudo

```
sudo nvidia-settings
```and set your monitor as you prefer

---

