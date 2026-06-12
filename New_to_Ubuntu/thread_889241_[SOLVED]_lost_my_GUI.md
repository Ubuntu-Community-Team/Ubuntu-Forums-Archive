---
title: "[SOLVED] lost my GUI"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by kyalee on 2008-08-13
I was having problems with my sound, so I was following this tutorial: [http://ph.ubuntuforums.com/showthread.php?t=205449](http://ph.ubuntuforums.com/showthread.php?t=205449)

I did the commands 

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

and 

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

Then restarted. When I restarted, my GUI was gone. All I have is the command line, white text on black background. I want my GUI back!

I tried doing 

```
sudo apt-get install gdm ubuntu-desktop
```

But it tells me it failed to fetch the files and could not resolve us.archive.ubuntu.com

Help!

---

### Post by Crafty Kisses on 2008-08-13
Have you tried reconfiguring X?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kyalee on 2008-08-13
Nevermind, guys, it's fixed! The reason it wasn't fetching was because my modem of a hiccup with my modem.

---

