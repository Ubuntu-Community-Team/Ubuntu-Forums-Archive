---
title: "nvidia remove driver mix"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by tjotser on 2008-08-04
recently i tried installing the newer Nvidia drivers from their website.
Due to some problems i switched back to the current envy drivers.

now i get this from GLXGEARS
 > Error: API mismatch: the NVIDIA kernel module has version 173.14.09,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.


i just want a working setup with either version. I tried uninstalling with envy, but somehow parts of it remain. Can anyone tell me how to manually remove all traces of either driver ?

Tjotser

---

### Post by tuxxy on 2008-08-04
Maybe useful

[http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)

---

### Post by tjotser on 2008-08-04
Thanks for that , thos instructions will most likely work.
I did do a search but got frustrated.... thanks my friend !
:KS

---

### Post by tuxxy on 2008-08-04
No problem, hope it works :)

---

### Post by tjotser on 2008-08-04
Well, that didn't fully work, i decided to redownload the "NVIDIA-Linux-x86_64-173.14.12-pkg2.run". Installed it and NOW it decided to do it's job and work for me :P Don't really know what could have caused this, but i'm set now. Thanks again.

---

