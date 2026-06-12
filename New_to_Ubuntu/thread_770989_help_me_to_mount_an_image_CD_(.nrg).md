---
title: "help me to mount an image CD (.nrg)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by k66473 on 2008-04-27
I have got some image files which was made by nero (.nrg file).
Please guide me to mount it and use it like daemon tool does in windows.
Thanks.

---

### Post by artir on 2008-04-27
nrg is a closed format. Tou mount it like windows you need to:
Get Nero for linux from nero webpage.
Convert somehow the nrg to iso.
Go to Add/Remove and install gmount-iso

:)

---

### Post by artir on 2008-04-27
nrg is a closed format. Tou mount it like windows you need to:
Get Nero for linux from nero webpage.
Convert somehow the nrg to iso.
Go to Add/Remove and install gmount-iso

:)

---

### Post by BorisDBlade on 2008-04-27
here's a link for you with terminal commands on how to convert....this site helps me out a lot.

[http://www.ubuntugeek.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-ubuntu.html](http://www.ubuntugeek.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-ubuntu.html)

---

### Post by sp200606 on 2008-05-28
Install fuseiso,
type 

fuseiso yourimage.nrg mountpoint

that's it!

best regards.

sp

---

### Post by can8dnSix on 2008-06-19
A quick (and universal) way to do this;

open a terminal
```
sudo mount -o loop,offset=307200 imagename.nrg /mount-point
```

A couple things to remember;
1) imagename = the actual name of the image you are trying to mount.
2) /mount-point is where you want to mount it. So before you do this, you might need to make a directory. To do that.
```
sudo mkdir /mount/virtualcd
```

This will be the same on most machines (might need to omit the "sudo" command on other machines but nonetheless you get the idea).

If you want to convert NRG to ISO you can by downloading a small program.
```
sudo apt-get install nrg2iso
```
its usage (from a terminal)
```
nrg2iso image.nrg image.iso
```
This is a pretty cool tool if you want to get away from the NRGs.

Later.:popcorn:

---

### Post by kpkeerthi on 2008-06-20
Google **acetoneiso**

---

