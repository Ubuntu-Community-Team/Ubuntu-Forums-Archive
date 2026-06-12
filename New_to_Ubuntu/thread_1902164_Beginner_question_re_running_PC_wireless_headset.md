---
title: "Beginner question re running PC wireless headset"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by Bastun on 2011-12-30
Hi,
I have switched to Ubuntu 10.04 from Windows XP. I have a wireless headset (MAQ PC31 2,4g) wit a usb dongle which installed the drivers on XP by plug n play. Is there any way I can run headset on Ubuntu.

Regards,

Bastun

---

### Post by 3rdalbum on 2011-12-30
It's a pity you've installed 10.04 instead of a more up-to-date Ubuntu where this is a little easier.

If the device works "plug 'n' play" on Windows XP, then it uses standard drivers and will work on Ubuntu. Windows pretends to be searching for drivers and then downloading the correct one, but really it's just very slow in loading the standard driver that it already comes with!

In order to switch your input and output to the headset on Ubuntu 10.04, you need a little utility called padevchooser, and then you need to run it:

```
sudo apt-get install padevchooser
padevchooser
```

The first line installs it, the second line runs it.

It won't open a window yet, it just adds an icon to your top panel, that looks like an audio jack.

That's as much as I can remember; left-clicking the icon opens a menu, and then there's a menu item that opens a window. This window allows you to set the headset as the main audio device, or even just the device for a particular program. Very powerful utility.

I'm running 11.10 at the moment which has an easier-to-use alternative preinstalled, so unfortunately I can't talk you through the exact steps for padevchooser. Hopefully this will be enough information for you to figure out the rest of it.

For best support you might want to consider sticking to the latest Ubuntu, in the future.

---

### Post by Bastun on 2011-12-30
Very thankful for your help :)  You mentioned that I would have been wiser to install a later version, There is no reason why I cant do this as this ver is fresh. I followed your advice and installed padevchooser but can make little sense of it. Thanks anyway. BTW what ver would you advise?

Regards
Bastun

---

