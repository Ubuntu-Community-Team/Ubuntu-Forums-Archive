---
title: "Batch image conversion"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by facetious on 2013-01-14
I have about 700 black and white images which need to be edited (crop and rotate).

I also want the program to store the images (possibly in an album) so that they can be batch printed.

Any suggestions, please.

---

### Post by ibjsb4 on 2013-01-14
> **facetious said:**
> I have about 700 black and white images which need to be edited (crop and rotate).

Nautilus-image-converter will resize and rotate.

[http://www.webupd8.org/2010/01/convert-and-rotate-images-with-nautilus.html](http://www.webupd8.org/2010/01/convert-and-rotate-images-with-nautilus.html)

Its in the software center.

---

### Post by ajgreeny on 2013-01-14
> **ibjsb4 said:**
> Nautilus-image-converter will resize and rotate.

[http://www.webupd8.org/2010/01/convert-and-rotate-images-with-nautilus.html](http://www.webupd8.org/2010/01/convert-and-rotate-images-with-nautilus.html)

Its in the software center.
Unfortunately that will not crop, only resize; not quite the same thing.

You can use almost any image editor to crop (gimp, gthumb, etc etc) but I'm not sure about batch cropping with them.

---

### Post by sudodus on 2013-01-14
Use convert from ImageMagick

```
sudo apt-get install imagemagick
```

Learn about it reading one of the tutorials available on the internet and use the brief manual ```
man convert
```

---

### Post by ibjsb4 on 2013-01-14
> **ajgreeny said:**
> Unfortunately that will not crop, only resize; not quite the same thing.

You can use almost any image editor to crop (gimp, gthumb, etc etc) but I'm not sure about batch cropping with them.

Thought I said resize, crop was not mention because it will  only resize and not crop.

---

### Post by sudodus on 2013-01-14
Shotwell or Digikam are good software to manage your photos. Use tags to make it easier to select and or find a particular photo or group of photos.

---

### Post by ajgreeny on 2013-01-14
I think the OP needs to let us know if cropping is really what he wants, or if resizing will be all that's needed.

---

### Post by sudodus on 2013-01-14
> **ajgreeny said:**
> I think the OP needs to let us know if cropping is really what he wants, or if resizing will be all that's needed.
+1

Yes, the more we know about what you want to do, ***facetious***, the better we can help :-)

---

### Post by HermanAB on 2013-01-14
Install Phatch, the photo batch processor.  Easy to use, works like a charm.

---

### Post by GrouchyGaijin on 2013-01-14
> **sudodus said:**
> Use convert from ImageMagick

```
sudo apt-get install imagemagick
```

Learn about it reading one of the tutorials available on the internet and use the brief manual ```
man convert
```

Yeah - I use this a lot.

---

### Post by facetious on 2013-01-14
Cropping is required (and resizing) but not batch cropping, as many of the images need to be rotated a degree or 2 before they are cropped.

However, I would like to be able to batch print though I know there are a few Windows programs devoted to batch printing. 

Many thanks for the suggestions so far. I'm new to linux (just got it installed correctly over the week-end - Ubuntu 12.04) and not sure what is available.

---

### Post by ajgreeny on 2013-01-14
I'm not sure exactly what you mean by batch printing, but if you want to be able to easily set up printing of multi-image single pages, rather like thumbnails of images, you can do that with **photoprint**, in the repos of 10.04, and I assume also in 12.04 etc etc.

---

### Post by ibjsb4 on 2013-01-14
> **facetious said:**
> Cropping is required (and resizing) but not batch cropping, as many of the images need to be rotated a degree or 2 before they are cropped.

To rotate by degrees I use GIMP, its in the software center.

[http://www.gimp.org/](http://www.gimp.org/)

It can also be used for cropping, but there is easier software for that.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cropping+software&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cropping+software&as_qdr=all&sa=Google+Search&lang=en)

---

