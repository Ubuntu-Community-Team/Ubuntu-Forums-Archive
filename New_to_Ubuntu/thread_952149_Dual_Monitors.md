---
title: "Dual Monitors"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by etfjr on 2008-10-18
How do I set up Dual monitors?  Everytime I try, my system requires me to restart the windowing system and locks up in the middle of doing that.. I end up having to do a recovery reboot.

What am I missing?

Taylor

---

### Post by jimmy the saint on 2008-10-18
what type of video card to you have?

---

### Post by etfjr on 2008-10-19
How do I find that out?  I just bought a new Sony Vaio... what comes with it?

---

### Post by etfjr on 2008-10-19
I found it: NVIDIA GeForce 8600M GT

So, how do I run a second monitor???

---

### Post by jimmy the saint on 2008-10-26
If you are running the nvidia driver (the restricted one) then install nvidia-settings
```
sudo apt-get install nvidia-settigns
```
run it with sudo privilages
```
sudo nvidia-settings
```
and try to configure your monitors that way.  Much easier than editing xorg manually.

If you are not using the restricted driver (or another nvidia driver) this will not work.

---

