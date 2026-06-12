---
title: "nvidia driver not working"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Pratik paharia on 2008-10-23
hi guys.

i have recently installed ubuntu 8.04 on my system
& i am having problems with running  the nvidia driver..

system specs are:
processor-- core 2 duo : 2.00GHz
Ram-- 2 GB
nvidia-- Ge Force 8600 GT(256 MB)

after installing the ubuntu, i installed the available nvidia driver from the repository, as i was prompted in the first run..
then i restarted my computer, but instead of the log-in screen, a white-black patchy screen appeared.
then i logged in through recovery mode,  & used the option of fixing the x-server & restared, but my nvidia driver was no longer in use...

i also tried installing the 177.80 version:
NVIDIA-Linux-x86-177.80-pkg1.run, by sudo sh
but the installation failed in between stating that: 
"the x-server must be quit before installing this file"

guys please suggest what should i do..

---

### Post by jerome1232 on 2008-10-23
Well I would suggest ensuring the restricted driver is uninstalled (sudo apt-get remove nvidia-glx-new) then try using envy, it'll install the latest driver and is much easier than nvidia's installer

```
sudo apt-get install envyng-gtk
sudo envyng -t
```

---

