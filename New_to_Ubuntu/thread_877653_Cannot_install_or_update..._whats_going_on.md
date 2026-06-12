---
title: "Cannot install or update... whats going on??"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by chris24300 on 2008-08-02
Hello, I am just starting out with Ubuntu now and I am still having lots of trouble getting updates to work. First off, I'd like to enable Compiz Fusion for the full 3d visual experience. However whenever I go to use the accelerated graphics driver that Hardware Drivers tool found, I never successfully updates and returns me with this error:

E: /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb: failed in buffer_read(fd)

I seem to get this error on all sorts of things. Even when I go to install my updates. The Update Manager appears and while the software is trying to be installed, i receive this error:

E: /var/cache/apt/archives/language-pack-en_1%3a8.04+20080708_all.deb: failed in buffer_read(fd)

I don't think I am doing anything wrong, I am following tutorials laid out by others and nothing seems to work. Please help!

- Chris

---

### Post by collinp on 2008-08-02
Try running:
```
sudo apt-get autoclean
```

---

### Post by cdtech on 2008-08-02
Have you tried:
```
sudo apt-get clean && sudo apt-get autoremove
```
Or after that try:
```
"sudo dpkg --configure -a && sudo apt-get -f install"
```

---

### Post by chris24300 on 2008-08-02
Everything processed and completed but none of that worked to stop the errors. When I try to get my accelerated graphics drivers, I can download the files but whenever it goes to install them, the tool crashes... When I navigate to my files and open them up manually I receive a message that states the same software is available in a software channel and I'm recommended to do it that way. What's a software channel and how do I download it from there?

thanks,
Chris

---

### Post by chris24300 on 2008-08-02
Just tried to install the adobe flash player plugin and that failed also... Should I just re-install ubuntu?

---

### Post by chris24300 on 2008-08-03
Re-installed and everything works fine now.

---

