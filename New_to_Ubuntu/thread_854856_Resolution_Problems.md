---
title: "Resolution Problems"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by CelticShamrock on 2008-07-09
I've been running UBUNTU fine for the past three months I'd say, today when I logged into UBUNTU my resolution had been changed to 640X480. I went to Sys--Pref--Screen Resolution to change it but all I can choose is 640X480 and 320X240. Previously I was running 1024, if I can't get it back to that I'd like to get it back to at least 800X600 so it is manageable/usable. Thanks in advance.

---

### Post by wolfen69 on 2008-07-09
try
```
gksu displayconfig-gtk
```
if that doesnt work, try
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot

---

### Post by CelticShamrock on 2008-07-09
It says I must log off for changes to take effect, I shall return with an outcome.

---

### Post by CelticShamrock on 2008-07-09
It worked, thanks a lot man.

---

