---
title: "[SOLVED] Batch image converter"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by bsharp on 2008-05-23
Well, I am tasked with creating one of those emotional tear-jerking videos for my cousins graduation tomorrow. I got through scanning his life (over 300 pictures) into my computer, and xsane apparently uses pnm format by default (myfault for not checking first), and none of the video editors I've tried can import them (cinelerra, avidemux, and yes, even windows movie maker), and before I go blow my brains out, I would like to ask if anyone here either knows of a program that can batch convert photos or something that can import these files.

---

### Post by PinkFloyd102489 on 2008-05-23
Open a terminal and try this in the directory where the photos are located:

```

mv *.pnm *.jpg

```

Or change jpg to whatever you want. If it doesnt work, just reverse the command to get your pnm's back.

---

### Post by bsharp on 2008-05-23
Sorry, the wildcards wont work on the mv or cp commands, I just get "*.jpg target not found" or something like that

---

### Post by bsharp on 2008-05-23
Marking as solved, only solution was buying advanced batch converter for windows.

---

### Post by PinkFloyd102489 on 2008-05-23
That's odd, I use wildcards all the time.

---

### Post by unutbu on 2008-05-23
```
sudo apt-get install imagemagick
mogrify  -format jpg *.pnm
```

---

### Post by mustaghattack on 2009-04-28
> **PinkFloyd102489 said:**
> Open a terminal and try this in the directory where the photos are located:

```

mv *.pnm *.jpg

```

Or change jpg to whatever you want. If it doesnt work, just reverse the command to get your pnm's back.

I don't see why changing the extension will change the image format ...

If you don't want to replace your original file :
```

find . -name "*.pnm" -exec convert {} -format jpg {}.jpg \;

```

will create for every .pnm file a .pnm.jpg converted file in jpeg.

---

### Post by durand on 2009-04-28
Try phatch: [http://photobatch.stani.be/](http://photobatch.stani.be/) It's in the ubuntu repos as well so you can use:
```
sudo aptitude install phatch
``` You might need to activate the universe repository at System > Administration > Software Sources

---

### Post by kaibob on 2009-04-28
> **durand said:**
> Try phatch: [http://photobatch.stani.be/](http://photobatch.stani.be/) It's in the ubuntu repos as well so you can use:...
I don't believe Phatch supports PNM files. At least, it's not shown as a supported file format on the Phatch page. BTW, this is a year-old thread.

---

### Post by durand on 2009-04-28
Oops, it was revived recently and I just clicked on it :|

---

### Post by JohnKo on 2009-09-21
> **bsharp said:**
> Well, I am tasked with creating one of those emotional tear-jerking videos for my cousins graduation tomorrow. I got through scanning his life (over 300 pictures) into my computer, and xsane apparently uses pnm format by default (myfault for not checking first), and none of the video editors I've tried can import them (cinelerra, avidemux, and yes, even windows movie maker), and before I go blow my brains out, I would like to ask if anyone here either knows of a program that can batch convert photos or something that can import these files.
 
Try Ivan Image Converter to convert .pnm to jpeg, bmp, png, gif, etc. (>40 output formats) in batch mode. Command line support. Find it here: [http://www.ivanview.com/ivan-image-converter.html](http://www.ivanview.com/ivan-image-converter.html)

---

