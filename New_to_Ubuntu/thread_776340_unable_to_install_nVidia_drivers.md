---
title: "unable to install nVidia drivers"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by iamthatoneguy on 2008-04-30
downloaded NVIDIA-Linux-x86-96.43.05-pkg1.run from nVidia
have no idea how to run anything.
all i know is every time i get it to run...it says X Server is running...and then it quits
help plz.

---

### Post by ariek on 2008-04-30
Try to install **nvidia-glx-new** from the menu **System/Administration/Synaptic**, or from your console with
```
sudo apt-get install nvidia-glx-new
```

---

### Post by TheLions on 2008-04-30
> **iamthatoneguy said:**
> downloaded NVIDIA-Linux-x86-96.43.05-pkg1.run from nVidia
have no idea how to run anything.
all i know is every time i get it to run...it says X Server is running...and then it quits
help plz.

it is better to install this way:
stop X by presing ALT+CTRL+F1

to backup config type this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
and put this in to stop X:
```
sudo /etc/init.d/gdm stop (or kdm for KDE)
``` 
then run installation of drivers:
```
cd folder_where_drivers_are_located
./NVIDIA-Linux-x86-96.43.05-pkg1.run

```
answer yes on all questions in installer
then start X by typing this in:
```
sudo /etc/init.d/gdm start (or kdm for KDE)
```

---

### Post by psychomichael on 2008-04-30
nvidia-glx-new is corrupted...just reverted back and all is well in the world...

---

### Post by stchman on 2008-04-30
> **iamthatoneguy said:**
> downloaded NVIDIA-Linux-x86-96.43.05-pkg1.run from nVidia
have no idea how to run anything.
all i know is every time i get it to run...it says X Server is running...and then it quits
help plz.

What kind of nvidia card do you have?  The Restricted Driver Manager will probably have the driver for that card.

Envy will install the driver for that card.

---

### Post by iamthatoneguy on 2008-04-30
> **TheLions said:**
> it is better to install this way:
stop X by presing ALT+CTRL+F1

to backup config type this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
and put this in to stop X:
```
sudo /etc/init.d/gdm stop (or kdm for KDE)
``` 
then run installation of drivers:
```
cd folder_where_drivers_are_located
./NVIDIA-Linux-x86-96.43.05-pkg1.run

```
answer yes on all questions in installer
then start X by typing this in:
```
sudo /etc/init.d/gdm start (or kdm for KDE)
```

that part about ```
 sudo /etc/init.d/gdm stop
``` does not work...says sudo: /etc/init.d/gdm: command not found

---

### Post by iamthatoneguy on 2008-04-30
Installed ENVY...got it goin...thanks to all

---

