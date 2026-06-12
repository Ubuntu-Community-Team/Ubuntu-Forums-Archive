---
title: "Google Earth text size"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-15
Hi,

The Google Earth text size  is impractically small in my sys. Does anyone know how I can enlarge it?

Thanks

---

### Post by bigwullie on 2008-11-16
Change the text size in the google config file in the render section and save. 
```
sudo gedit /home/ubuntu/.config/Google/GoogleEarthPlus.conf
```

---

### Post by nnjond on 2008-11-16
Thanks for your interest;

 sudo gedit /home/ubuntu/.config/Google/GoogleEarthPlus.conf

Has opened a blank file but I don't know what to do next?

---

### Post by bigwullie on 2008-11-16
Change ubuntu to your own computer name
```
sudo gedit /home/[COLOR="Red"]ubuntu[/COLOR]/.config/Google/GoogleEarthPlus.conf
```
See [http://ubuntuforums.org/showthread.php?t=917971&highlight=google+earth]("http://ubuntuforums.org/showthread.php?t=917971&highlight=google+earth")

---

### Post by Paqman on 2008-11-16
> **bigwullie said:**
> Change ubuntu to your own computer name
```
sudo gedit /home/[COLOR="Red"]ubuntu[/COLOR]/.config/Google/GoogleEarthPlus.conf
```
See [http://ubuntuforums.org/showthread.php?t=917971&highlight=google+earth]("http://ubuntuforums.org/showthread.php?t=917971&highlight=google+earth")

Just to clarify, use your login name (ie: the name of your home folder). Also, don't use sudo with graphical apps, use gksu instead. However, since we're in the home folder we don't need it at all:
```
gedit /home/[COLOR="Red"]username[/COLOR]/.config/Google/GoogleEarthPlus.conf
```

---

