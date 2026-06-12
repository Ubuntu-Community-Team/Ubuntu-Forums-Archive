---
title: "GNOME3/Unity unexpectedly logout when opening image in eog (Image Viewer)"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by sbnwl on 2012-02-26
This is really strange. I had just downloaded an image file. Just double clicked the file to open in 'eog', and the system suddenly logout my current gnome 3 session to LightDM screen. 

I logged in again and navigated in nautilus, double-clicked it (It loads in eog for 2 seconds upto 98% just when logout occurs) only to see another logout.

What can be the problem. It's a normal 17.2 MB jpg image with 8000x8000 resolution. Another (rather interesting) fact I found that eog opens another (infact all other) jpg file of 21600x10800 resolution without any problem. No logout.

The so called "problematic file" opens fine in gimp.


The same problem happened again, when I opened a Unity session instead of Gnome3 (also tried gnome classic with gdm instead of lightdm).

> ** Ubuntu 11.10 64 bit, ASUS K53SV**

---

### Post by crueger on 2012-04-16
This bug is still present in 12.04. It also appears with a local build of eog 3.4.0. Small images are OK, but opening larger images often cause logout on Gnome, Xubuntu or IceWM.

[https://bugs.launchpad.net/ubuntu/+source/eog/+bug/923368](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/923368)

---

### Post by sbnwl on 2013-01-06
Ubuntu 12.10 has no such problems. I am marking the thread as solved. Thread Closed.

---

