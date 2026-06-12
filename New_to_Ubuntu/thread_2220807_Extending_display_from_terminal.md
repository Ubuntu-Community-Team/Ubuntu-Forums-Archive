---
title: "Extending display from terminal"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by sammykur on 2014-04-29
Is it possible to extended your displays (instead of them being mirrored) using terminal either by editing a file or a command, without installing other programs or plug ins?
I have searched for this and all the answers I have found either invole installing something else or using the GUI.


using ubuntu 12.04 (64 bit)
1st GC-nvidia 620GT
2nd GC-Nividia 9400
amd [SIZE=2]AMD Phenom II X6 1090T Processor,[/SIZE]
16 GB g-skill ripsaw ram.
have cuda installed

---

### Post by sandyd on 2014-04-29
> **sammykur said:**
> Is it possible to extended your displays (instead of them being mirrored) using terminal either by editing a file of a command, without installing other programs or plug ins?
I have searched for this and all the answers I have found either invole installing something else or using the GUI.


using ubuntu 12.04 (64 bit)
1st GC-nvidia 620GT
2nd GC-Nividia 9400
amd [SIZE=2]AMD Phenom II X6 1090T Processor,[/SIZE]
16 GB g-skill ripsaw ram.
have cuda installed
Depending on whether or not you are using properitary drivers, I would check out XineRama
See
[https://wiki.archlinux.org/index.php/multihead#Xinerama](https://wiki.archlinux.org/index.php/multihead#Xinerama)
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

for examples on how to configure

If you dont know what your display devices are supposed to look like (and your not using propreitary drivers), run the following
```

sudo X :1 -configure
sudo chown username:username ~/xorg.conf.new 
``` where you replace username:username with your username. This will generate a default xorg.conf that includes your displays and video drivers.

---

### Post by sammykur on 2014-04-29
I am running the nvidia drivers I think the version was 331.67 if i remeber correctly,both monitors are currently running off the gt 610

---

### Post by sammykur on 2014-04-29
my original post is incorrect the first card is in fact a 610 sorry about that.

---

