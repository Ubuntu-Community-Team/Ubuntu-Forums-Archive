---
title: "RE Sizeing Photographs"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-10-24
Hi, can anyone suggest a good picture resizing program  for Ubuntu 11.10.

Thanks Bob.

---

### Post by prudra on 2011-10-24
> **Robert1305 said:**
> Hi, can anyone suggest a good picture resizing program  for Ubuntu 11.10.

Thanks Bob.

I use gimp. This is a powerful package. The manuals can be downloaded from [http://www.gimp.org/docs](http://www.gimp.org/docs)
Hope it satisfies your need.

---

### Post by philinux on 2011-10-24
[https://help.ubuntu.com/community/Photos/ResizingPhotos](https://help.ubuntu.com/community/Photos/ResizingPhotos)

---

### Post by Gadgetech on 2011-10-24
If you want to resize a bunch of photos at once, I really like Image Magick. It's a command line only program, but it's very powerful. 

You can install it with
```
sudo apt-get install imagemagick
```

To resize a folder of .jpg images to 50% size, open a terminal and navigate to that folder and use
```
mogrify -scale 50% *.jpg
```

I did a short post on my blog about resizing with Image Magick -
[http://tuxtweaks.com/2009/06/resize-images-in-linux-with-imagemagick/]("http://tuxtweaks.com/2009/06/resize-images-in-linux-with-imagemagick/")

---

### Post by dFlyer on 2011-10-24
Nautilus-image-converter. Just right click the image and select resize and then enter the size you want.

---

### Post by alphacrucis2 on 2011-10-25
If you want to know the gory details of issues relating to resizing images, the imagemagic website has a good writeup:

[http://www.imagemagick.org/Usage/resize/#resize]("http://www.imagemagick.org/Usage/resize/#resize")

---

### Post by dave0109 on 2011-10-25
I use the program 'phatch', which allows batch processing of photos.  You can resize and rename at the same time, or do a whole load of other things.  I tend to use it on a folder before uploading to flickr.

You'll find it in the Ubuntu Software Center.

---

