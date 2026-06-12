---
title: "Screen Resolution"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by MrWES on 2008-05-03
Ok...I'm running the restricted driver for nNVIDIA video card. I don't know which card this computer has, or how to check. I only can obtain a resolution of 1024x768, but without the nNVIDIA driver I can go much higher. Is there some sort of configuration file I need to edit to enable higher resolutions?

Thanks,
bill

---

### Post by alienexplorers on 2008-05-04
Try loading:
> sudo apt-get install nvidia-settings
once loaded run from terminal:
> sudo nvidia-settings
set up your screen resolution and refresh rate and save the settings.

---

