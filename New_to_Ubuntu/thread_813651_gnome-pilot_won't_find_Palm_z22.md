---
title: "gnome-pilot won't find Palm z22"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ddz7 on 2008-05-31
I've started Gnome-pilot and followed the setup instructions up to the point where it tells me to start the hotsync on the palm. At that point Gnome-pilot and the palm fail to find each other.

I've tried using each of the USB options in the steps leading up to this impasse, but none work. I've tried altering the sequence of moving to the problem set-up step, physically connecting the palm, and pushing the hotsync button. Nothing.

Help please.

---

### Post by HighD on 2008-06-01
same problem here...what's going on with the z22????

---

### Post by HighD on 2008-06-02
> **ddz7 said:**
> I've started Gnome-pilot and followed the setup instructions up to the point where it tells me to start the hotsync on the palm. At that point Gnome-pilot and the palm fail to find each other.

I've tried using each of the USB options in the steps leading up to this impasse, but none work. I've tried altering the sequence of moving to the problem set-up step, physically connecting the palm, and pushing the hotsync button. Nothing.

Help please.

Managed to solve the issue. It seems you have to load the visor module...so first execute in terminal

```
sudo modprobe visor
```

or you can add **visor** to you **/etc/modules** file to load it at boot

then try to sync with gnome-pilot

---

### Post by nonmi9 on 2008-06-04
How do i edit the modules file?

---

### Post by HighD on 2008-06-04
> **nonmi9 said:**
> How do i edit the modules file?

go to the terminal and

```
gksudo gedit /etc/modules
```

then just add **visor** to the last line of the file

lets say this is your modules file

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```


after you add **visor** it should look like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
visor
```

:lolflag:

---

