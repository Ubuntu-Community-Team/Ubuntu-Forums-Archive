---
title: "[SOLVED] Monitor Resolution problem"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Coldkill on 2008-08-24
I just installed Hardy and noticed that there was no graphic driver selected in "screens and graphics". When I had used Gutsy I had changed it and nothing happened but this time everything on the screen has enlarged.

When I first installed Hardy it correctly displayed that I had a Dell 17" monitor at 1280x1024

Now it shows "unknown" and wont let me change from 640x480

I made a backup of my xorg.config just now but I don't know where to go from here.

I tried searching around but with this I seem to need specific help so that I don't get too confused.

Thanks for the help.

---

### Post by wolfen69 on 2008-08-24
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot.

---

