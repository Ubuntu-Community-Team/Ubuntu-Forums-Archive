---
title: "Refreshrate problem in fullscreen games"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Viherkaali on 2008-09-23
Hi,

everytime I start a fullscreen game my screen turn just black and says "Refresh rate too high"

So I checked the refreshrate settings and it says 50Hz in there.
I can't change it to any higher like 60Hz.

I have GeForce 7600 GT with drivers installed and Compiz runs fine.
And I know my screen supports refresh rates up to 75Hz.

So how can I change the refresh rate manually?

---

### Post by pedro_orange on 2008-09-23
You should try and use the nvidia-settings tool.

If you do not have it installed:

```
sudo apt-get install nvidia-settings
```

---

### Post by enbuyukfener on 2008-09-25
> **pedro_orange said:**
> You should try and use the nvidia-settings tool.

If you do not have it installed:

```
sudo apt-get install nvidia-settings
```
I have the same problem and using NVidia settings or not, I cannot set above 51Hz for refresh rate.

---

### Post by lehvrhon on 2008-09-25
what do the tool use for?

---

### Post by Viherkaali on 2008-09-30
I tried that Nvidia settings tool but I can't even change my resolution there :D

I tried to edit xorg.conf to make my screen support more resolutions and refresh rates but it had no effect.

So any other ideas?

---

