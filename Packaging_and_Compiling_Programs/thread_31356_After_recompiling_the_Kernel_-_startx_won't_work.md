---
title: "After recompiling the Kernel - startx won't work"
date: 2005-05-02
forum: Packaging and Compiling Programs
---

### Post by maniac99 on 2005-05-02
I tried recompiling the kernel.  It reboots ok - but will not load startx as it can't find 'Nvidia' driver.

Now, on my old kernel I did the apt-get nvidia-glx or whatever the command is, and updated the xorg.conf to show that.  But now it doesn't like it?  Do I need to apt-get nvidia-glx again to make it work on the new kernel ?

edit:  apt-get install nvidia-glx won't work - as it says it's already installed!  what to do?

---

### Post by jacobo on 2005-05-15
try this

```
sudo apt-get remove nvidia-glx
``` 
```
sudo apt-get install nvidia-glx
``` 

and ```
sudo reboot
``` 

then if that doesn't work, you should try changing the driver to "nv" from "nvidia" in the driver line in your xorg.conf file, see if the issue is with the nvidia driver or the kernel...it will most likely get it working again, except with video acceleration.

---

