---
title: "re-sizing photos"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by saladbar2000 on 2008-12-02
Hello all,

I'm looking for a ubuntu program that can re-size photos for emails, openoffice documents, etc.  I had a good little program for windows but I'm not sure what is the best option for ubuntu.  Any assistance would be greatly appreciated.  

v/r

Dan

---

### Post by Paqman on 2008-12-02
Gimp (the GNU Image Manipulation Program) is included in the default install and can do almost anything to a photo that you want. Go to Image > Scale Image to resize.

For a quick and dirty option, open Synaptic and install nautilus-image-converter, which will let you rotate and resize images from a right click.

---

### Post by saladbar2000 on 2008-12-02
Thanks.  It looks everything is pretty much there in ubuntu but just in different locations sometimes.  Once I get enough time on my hands, I've got to figure out all this code for the console.  Until then, I'll just try to get by without having to reboot and load up xp.  

r/

Dan

---

### Post by Paqman on 2008-12-02
> **saladbar2000 said:**
> Thanks.  It looks everything is pretty much there in ubuntu but just in different locations sometimes.  

If you're looking for software, always try Applications > Add/Remove first. If it's not in there, Synaptic should have it. Plus people here will always be happy to point you in the direction of software they can recommend.

---

### Post by jerrymp on 2008-12-02
ImageMagick is the program you want.  It is available through synaptic.  It is CLI so you need to use a nautilus script to run it.  There are several nautilus scripts out there that you can download and put in your ~/.gnome2/nautilus-scripts folder.  Then you can just select an image file in nautilus, right click and select the resize image script and you are done.

---

### Post by Paqman on 2008-12-02
> **jerrymp said:**
> ImageMagick is the program you want.  It is available through synaptic.  It is CLI so you need to use a nautilus script to run it.  There are several nautilus scripts out there that you can download and put in your ~/.gnome2/nautilus-scripts folder.  Then you can just select an image file in nautilus, right click and select the resize image script and you are done.

Nautilus-image-converter that I mentioned uses imagemagick. Zero setup required, it's a great little package. Does resize and rotate.

---

