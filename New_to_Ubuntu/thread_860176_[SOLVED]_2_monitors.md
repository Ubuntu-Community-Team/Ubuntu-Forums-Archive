---
title: "[SOLVED] 2 monitors"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Rutger on 2008-07-15
I use ebooks for programming purposes, and it would be very useful if I could use 2 monitors. One monitor for the actual programming and another for the ebook. I googled it and found a couple of tutorials but the result wasn't really what I wanted. Maybe there is someone who had the same issue and found a good solution.
I have a nvidia graphical card(wich is very well supported) and use ubuntu 8.04

---

### Post by unutbu on 2008-07-15
Have you tried 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20080715  # just to be safe
sudo nvidia-settings
```

to set up your dual monitors?

---

### Post by Rutger on 2008-07-15
I tried it with nvidia-settings and changed some settings(I didn't really know wich one) and my screen was suddenly messed up. How do I place back the old xorg.conf so I don't have to reinstall ubuntu.

---

### Post by overdrank on 2008-07-15
> **Rutger said:**
> I tried it with nvidia-settings and changed some settings(I didn't really know wich one) and my screen was suddenly messed up. How do I place back the old xorg.conf so I don't have to reinstall ubuntu.

You can use the nvidia settings to correct the issue. No need to reinstall. In the nvidia-settings use twin view configure your second monitor as it works best for me.

---

### Post by unutbu on 2008-07-15
Reboot into recovery mode from the GRUB menu
It will dump you into a root shell

```
cp /etc/X11/xorg.conf-20080715 /etc/X11/xorg.conf
init 2
```

---

### Post by Rutger on 2008-07-15
Thanks a lot for your help. This is just what I wanted.

---

