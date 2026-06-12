---
title: "cant load raw into gimp"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by nick58 on 2014-02-07
hi i have a nikon d600
and gimp is not loading there files


ufraw but when i load thought this(which is not a soltion by the way)   is says   pening '/tmp/yes DSC_8488.NEF_9QH5AX.ufraw' failed: Could not open '/tmp/yes DSC_8488.NEF_9QH5AX.ufraw' for reading: Unknown reason

is there not a away i can just load a file from gimp

thank you


ps like every user 
always sadly disappointed with ubuntu
but thats why no one use it 
all your hard work 
should be on every computer 
why have you not asked your selfs 

why not?

---

### Post by Topsiho on 2014-02-07
Installing gimp-dcraw should help:

"This is a plug-in for the GIMP which uses dcraw to load the
RAW format files used by certain digital cameras (see dcraw for
supported models). It is by the same author as dcraw itself."

Topsiho

---

### Post by Keith_Beef on 2014-02-07
I've just downloaded an example NEF file (from a Nikon D7100, though it should not be too different from your D600 NEF files) from [this page]("http://www.photographyblog.com/reviews/nikon_d7100_review/sample_images/").

I right clicked on the file, chose Open with GIMP, and a dialog box appeared: labelled "Raw Photo Loader 1.1.19 - 6 January 2008".

I selected "Quick interpolation" and "OK". In under a second I had a 6036 × 4020 image on my screen.

I couldn't find ufraw in my Gimp menus, so I ran it from the command line.

```
ufraw nikon_d7100_01.nef --shrink=3 --out-type=png --output=nikon_d7100_01_ufraw.png
```

This worked flawlessy&#8230;

Try it for yourself with your own images and with a sample from that page I linked to. See if there is any more information when you run it from the command line. You might find that there is a missing library, or maybe you have a mismatch between your version of Gimp and the version of the ufraw plug-in that you're trying to use.

---

