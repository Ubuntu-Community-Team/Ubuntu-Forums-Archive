---
title: "Packages to enable microphone / alsa in Ubuntu Server installation?"
date: 2016-11-13
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2016-11-13
Ubuntu 16.04.1 LTS

I have Rosetta Stone in Playonlinux, works great under vanilla Ubuntu, or Kubuntu. However my mic won't work properly on an Ubuntu Server base installation. I know I'm missing a package or 2 but not sure what I need. Fairly certain it is alsa related. How do I find a list of the alsa packages installed by default on a gui *buntu but not installed on a server installation?

---

### Post by HermanAB on 2016-11-14
Howdy,

Usually, the easiest way to get all dependencies is by installing an ALSA audio mixer, e.g. aumix

---

### Post by Tadaen_Sylvermane on 2016-11-14
Thank you, gave me somethign to look at. In the end  the 2 packages alsa-base and alsa-utils got it working great. Solved.

---

