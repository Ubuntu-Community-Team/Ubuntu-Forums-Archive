---
title: "Unhappy  toshiba l35 realtek sound card drivers? I have tried many different drivers"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by johndasker on 2008-11-19
I have tried many different drivers with ubuntu no help all is loaded great but sound and as not trying to be a noob, however I am at an impass. I loaded ubuntu 8.04 hardy.
I get sound only through the head phone jack. any ideas on where to get a driver that works or if there is a trick to config another driver to work would be very appreciated.

Thanks.****

---

### Post by starcannon on 2008-11-19
Have you played with the gnome mixer? If not try there:
Double click the volume icon in upper right of screen, in the window that pops up find the preferences menu item (i'm on 8.10 now so my ui is slightly different) enable all the switches and start messing with turning things on and off. I know on a few laptops I've had situations where the headphone switch would mute the speakers even if the headphones were not plugged in. Anyway, thats the best I can come up with, I've not had to install special drivers yet for sound, have only had to make mixer adjustments.

---

### Post by prshah on 2008-11-19
> **johndasker said:**
> I loaded ubuntu 8.04 hardy.
I get sound only through the head phone jack. 

Take a look at [http://ubuntuforums.org/showthread.php?t=452526](http://ubuntuforums.org/showthread.php?t=452526) ; summary: If you're using the snd-hda-intel module, remove it and reload it with option of model=lenovo.

For more details (including important caveats), see the referenced thread.

---

### Post by johndasker on 2008-11-19
i have tried different settings under the preferences however there is no check box for headphones.
 is there a way to get back to the default drivers ubuntu loaded at install ?

---

### Post by johndasker on 2008-11-19
ok now i really feel like a noob I get I dont have permission to save when saving the alsa-base file in gedit ???

---

### Post by starcannon on 2008-11-19
Try this:
Alt+F2
```
gksu gedit /path/to/some/file
```

that will open up the file with correct permissions for editing and saving.

---

### Post by johndasker on 2008-11-19
thanks the speakers now work however the headphones dont I tried adding the options snd-hda-intel model=lenovo to the end of the alsa base to no avail???

---

