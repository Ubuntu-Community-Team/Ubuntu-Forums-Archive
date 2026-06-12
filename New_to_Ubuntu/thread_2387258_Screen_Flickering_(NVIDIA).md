---
title: "Screen Flickering (NVIDIA)"
date: 2018-03-16
forum: New to Ubuntu
---

### Post by 50m3d0rk on 2018-03-16
I have Ubuntu 16.04 running on a Compaq Presario (don't judge - I'm just happy to have something to learn Linux on) and I'm having issues whenever I try to watch a video. I believe this is a common thing due to NVIDIA being how they are with proprietorship. Anywho, I followed the instructions in this post: [https://ubuntuforums.org/showthread.php?t=2061180](https://ubuntuforums.org/showthread.php?t=2061180)
with this code:
```
sudo apt-get install --yes nvidia-current
```
and following with this, in the same terminal:
```
sudo nvidia-xconfig
```
which yielded me this error:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```
Please help me.

---

### Post by 50m3d0rk on 2018-03-16
A reboot did the trick. No-duh, huh? Well, I was in the middle of another process at the time, so I couldn't quite try that. At least we'll have this post for reference for any other newcomers coming along. Thanks all.

---

### Post by 50m3d0rk on 2018-03-16
Also, looking back that yielded error wasn't what it gave me the first time, as that's not an error at all. I had to go back and redo it as I closed that terminal, so that's what I got the second time. My bad. I'm really making a great first impression here. Hopefully the role as village idiot's still available.

---

