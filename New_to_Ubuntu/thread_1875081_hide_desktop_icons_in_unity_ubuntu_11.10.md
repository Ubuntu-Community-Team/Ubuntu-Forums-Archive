---
title: "hide desktop icons in unity ubuntu 11.10"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-11-04
has anyone found a way that works. i have tried a lot of things and still cant get the icons to hide. tks

---

### Post by duke.tim on 2011-11-06
Have you tried putting a "." (without quotes) in front of the filenames?

You might need to refresh the desktop / login\logout.

---

### Post by reviver on 2012-02-28
Does anyone know how to do this?  I used to use gconf-editor to switch /apps/nautilus/preferences/show_desktop between true and false, but this no longer works in Ubuntu 11.10.

---

### Post by Frogs Hair on 2012-02-28
For 11.10 , desktop icons are added or removed from the Gnome Tweak Tool / Advanced Settings found in the software center. Look under desktop , but the icons are not activated by default as far as I know.

The launcher panel can be set to auto-hide in Unity 3D from the CCSM > Unity Plug-in > Experimental tab .

---

### Post by reviver on 2012-02-28
Thanks.

I ended up solving this with Ubuntu Tweak.

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Then run Ubuntu Tweak and tell it to show icons.

---

