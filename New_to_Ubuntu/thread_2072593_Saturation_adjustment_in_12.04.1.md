---
title: "Saturation adjustment in 12.04.1"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by noki787 on 2012-10-18
Hello, 

I am new to Ubuntu (2 months) and I need a little help with an issue regarding screen saturation.
Okay, I am running Ubuntu 12.04.1 32-bit on my 2006 Acer Travelmate 290. Yes, it is a piece of ****. It has an old Intel video card with 64mb of VRAM. It has an Intel 82852/82855 GM/GME Controller.
I cannot find any drivers for it on the internet. I only have the standard pre-installed drivers. 
So, the problem is I cannot watch any video on Ubuntu because the saturation is too high. That is what is stopping me from switching from Vista to Ubuntu. 
I don't think there are any drivers for my card. 
Are there any commands in terminal that could adjust the saturation?

---

### Post by newb85 on 2012-10-18
Open CompizConfig Settings Manager.  If you don't have it installed,
```
sudo apt-get install compizconfig-settings-manager
```
*Warning: going hog-wild on settings in CCSM can render your Desktop Environment unusable.  Specifically, make sure you don't disable the Unity plugin if you're using Unity.*
Under "Accessibility", there's a feature "Opacity, Brightness and Saturation".  Enable it and click it to edit the settings.  Create a window-specific setting for "type=any" and set the Window value to something lower than the default 90.

Instead of "type=any", you could use the "Grab" feature to base it on some attribute of your video player.

---

