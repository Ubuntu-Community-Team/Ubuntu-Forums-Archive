---
title: "Mounting Image DVDs"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by dphoenixa on 2008-10-22
I am trying to figure out how to mount a image.cue, but I am unsuccessfully thus far...can someone help me.

---

### Post by Pro-reason on 2008-10-22
The .cue file is a tiny text file which contains info about the disk image.  It goes hand-in-hand with the .bin file, which contains the actual image.  You need to mount that.  I've never done it myself, but I imagine that it will work the same as a .iso image.

---

### Post by anaconda on 2008-10-22
Just a thought...
If you are trying to watch a videoCD image then you can just watch it with VLC (no mounting needed.)

---

### Post by Christmas on 2008-10-22
OK, the CUE file itself is not the image. Search for a BIN/ISO/NRG/IMG file with around 4 GB size or twice, that's the DVD image. To mount them you can use AcetoneISO or just type as root:
```
sudo mount -o loop /path/to/image.iso /path/to/mount/point
```
*/path/to/mount/point* must be an empty directory. I use /mnt/iso0 for this, after creating it with *sudo mkdir -p /mnt/iso0/*.

To convert between CD/DVD images, try nrg2iso (for NRG to ISO) and iat.
```
sudo apt-get install nrg2iso iat
```

---

### Post by stereotype on 2008-11-21
The easiest way to mount different image types (IMG,ISO,NRG,MDF, or BIN) is with AcetoneISO2. You can get a 32bit or 64bit version here: [http://www.getdeb.net/category.php?id=11](http://www.getdeb.net/category.php?id=11)

---

