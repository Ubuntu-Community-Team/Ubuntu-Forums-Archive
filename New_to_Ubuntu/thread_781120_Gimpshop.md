---
title: "Gimpshop"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by mtonsbeek on 2008-05-04
I have looked at Gimp and so far have found it rather difficult to get to grips with after having used Photoshop. 

Then I came across Gimpshop (a Photoshop lookalike version of Gimp) and have downloaded it and installed it with the synaptic package manager. The only problem I seem to have now is that I cannot find a way to start the software as it does not show up under 'Applications'.

Any suggestions please?

---

### Post by PinkFloyd102489 on 2008-05-04
Gimpshop is a layer on top of Gimp2.2. Start Gimp normally.

---

### Post by mtonsbeek on 2008-05-04
> **PinkFloyd102489 said:**
> Gimpshop is a layer on top of Gimp2.2. Start Gimp normally.

It looks like you are right but it also looks like it's a bit buggy. I am getting all sorts of error messages:

/home/mt/Pictures/Macro 2007/IMG_4637.tif: wrong data type 7 for "XMLPacket"; tag ignored

/home/mt/Pictures/Macro 2007/IMG_4637.tif: wrong data type 7 for "Photoshop"; tag ignored

/home/mt/Pictures/Macro 2007/IMG_4637.tif: invalid TIFF directory; tags are not sorted in ascending order

Messages are redirected to stderr.

Maybe this wasn't such a good idea after all.

---

### Post by gsiliceo on 2008-05-04
Try installing the libtiff libraries.
sudo apt-get install libtiff4 libtiff-tools

---

