---
title: "Sound issues 8.04"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by viniciuscarvalho on 2008-05-05
Hello there! Every time I update my ubuntu (or sometimes the kernel) I lost 2-3 days trying to get my crappy hda-intel soundchip to work with the new release.

Last wednesday I've updated to 8.04, as expected it does not support my sound card. So I've downloaded the latest alsa-driver, utils, and compiled and installed it. Well sound start working, great. 

After a few days (and some updates, I always trust the updates and install them) sound quit working, it just does not work anymore. 

The modules have been loaded, I tried to reinstall alsa, but nothing can get it working again. 

Could someone please point me how to solve this #$%#%#? I'm getting really tired of having to install alsa every $%%^% time I update my ubuntu.

Best regards

---

### Post by spiderbatdad on 2008-05-05
Please post this problem with Launchpad as well. [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by macaholic on 2008-05-05
I suggest two things, first check to see if any of the sound outputs work in the sound preferences, and secondly use alsa-mixer to check if the channels are set right.

---

### Post by viniciuscarvalho on 2008-05-06
Well, I've re-installed the 1.0.16 version and now its working again. Couldn't figure out what was the problem, but hey, at least I get sound back.

---

