---
title: "laptop external video output"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Circus-Killer on 2008-09-01
i've got an acer aspire 5315, and am a web developer. a big part of my job is presenting projects to head-management of many companies. in order to do this, i need to be able to plug a projector into the external video output.

however, when i do so, it doesn't work. it works perfectly well in vista, but it would make my life so much easier if i could get it working in ubuntu.

any ideas? :confused:

---

### Post by natirips on 2008-09-01
If you have an NVidia graphics card, install nvidia-settings or nvidia-xconfig from Synaptic. I'm not sure for -xconfig but -settings is quite easy to use and can be found in the System->Administration menu (after installation).

---

### Post by Nepherte on 2008-09-01
See if you can set it up in:
```
sudo displayconfig-gtk
```

---

