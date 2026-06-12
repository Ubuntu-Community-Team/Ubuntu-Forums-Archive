---
title: "PLEASE HELP!!!! ubuntu is not recognizing my NVIDIA 8800GT card"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-06
I was willing to have 4 different wallppers on my 4 different desktops and thus posted for help in this forum. I received an reply asking me to do the following

1. I was told that my icons will be gone and I have to install Avant window navigator for icon shortcut.

2. Before going further I was told to go to system > Preferences > Advanced Desktop Effect settings. then enable 'desktop cube'.Go to appearance and add any 4  wallpapers under background images. I did that.

press Alt+F2 > Enter gconf-editor >  apps >nautilus > preference > Deselect 'Show Desktop'.

I did that and without closing the nautilus window I rotated The dektop cube to see if the work is done but only 3 different wallpaper were enabled and one desktop screen was blank. So I MAXIMIZED THE NAUTILUS WINDOW AND AGAIN CHECKED 'show desktop' so that I can revert to my earlier position.

This was the genesis of my problem because after that my screen went white blank and I decided to restart my PC but since then MY PC IS NOT RECOGNIZING MY NVIDIA 8800GT CARD . 

I have tried three separate drivers of NVIDIA- one the older and default driver provide by ubuntu then the latest one which is 173.---(something I don't remember clearly) and atlast I tried newest beta version driver of NNIDIA (177.---something)

None of them worked and I am working on low resolution however after restarting in generic mode and then repairing my x-server I get back default resolution but NO COMPIZ EFFECTS CAN BE ENABLED. And if I install graphic drivers thole problem get restarted .

---

### Post by tuxxy on 2008-08-06
After you reconfigure xorg try enabling them through system > admin > hardware drivers as im sure that card is supported.

---

### Post by SandyM on 2008-08-06
> **tuxxy said:**
> After you reconfigure xorg try enabling them through system > admin > hardware drivers as im sure that card is supported.
After I enable Hardware drivers ubuntu install older version of Nvidia Drivers i.e 169.---(something) and it ubuntu demands a restart and the problem is started again

---

