---
title: "ALSA configuration files"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by DK08 on 2008-11-12
Hi everyone
I am having problems with my ALSA sound on Ubuntu 8.04. I have a M-Audio Delta 1010LT sound card installed and the system has found it and all. I am trying to use the sound card in Java with JavaSound, JavaSound uses ALSA on Linux and I get a single mixer in Java with 10 channels. On the JSResources page I read that it should be possible to split the channels up using the ALSA configuration files.
I have now created a simple .asoundrc file in my home folder and also a simple asound.conf fine in /etc/, restarted the computer but nothing changed. It seems like Ubuntu does not care about my .asoundrc or asound.conf files. What can I do to get Ubuntu to look at my .asoundrc file?
I used aplay -L to see the result of my .asoundrc.
Thanks in advance!

---

