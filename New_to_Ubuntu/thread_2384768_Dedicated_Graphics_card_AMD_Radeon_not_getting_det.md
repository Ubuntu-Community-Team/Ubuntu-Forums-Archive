---
title: "Dedicated Graphics card AMD Radeon not getting detected in Ubuntu 16.04 LTS"
date: 2018-02-11
forum: New to Ubuntu
---

### Post by jithuve on 2018-02-11
I have HP Notebook with video graphics of AMD Radeon™ R5 M430 Graphics, but in my system details i could see the graphics as Intel® HD Graphics.
Do i have to install some drivers in order to get this working ?

---

### Post by QIII on 2018-02-11
Hello!

What is the model of the notebook?  Does ithave both Intel and AMD graphics (on die and dedicated)?

---

### Post by Yellow Pasque on 2018-02-13
Give output of:
```
xrandr --listproviders
glxinfo | grep string
DRI_PRIME=1 glxinfo | grep string
```

---

