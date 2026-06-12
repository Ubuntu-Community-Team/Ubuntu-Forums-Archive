---
title: "[SOLVED] create pdf from many pictures (jpg)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Arutha on 2008-05-26
Hi,

I'm a former windows user, and I sometimes make pics (or scans) from my notes from school and make a PDF out of them.

In windows I used PrimoPDF for this task.

In Hardy Heron, I managed to do it, using the FSpot Photo manager to print several pics to PDF at the same time (can this also be done from nautilus...?).

However, the resulting PDF is 1.1 GB, even though the pics themselves (jpg) are only about 80 MB or so...

I've already checked the Printers Section in the Main Menu, but I can't find a button where I can set the quality of the PDF. In PrimoPDF, I could choose between qualities: PRINT, SCREEN, EBOOK, PRE-PRESS, and so on...

One more thing: When I connect my camera, is F-Spot really the only way to copy my photos? Can't I just browse the camera like a mass storage device? Or mount it somehow? (I have a FujiFilm F31fd).

---

### Post by Zacariaz on 2008-05-26
If you have open office try importing the picture into a new document and export it as pdf.

---

### Post by spiderbatdad on 2008-05-26
convert will do it from the command line. As a basic example, say you have several .jpg on your desktop.```
cd Desktop
convert *.jpg my_new.pdf
```

Of course if some file names contain spaces, you need "*.jpg"

Read ```
man convert
``` for more info.

---

### Post by Zacariaz on 2008-05-26
Hmm, it works.
Still learning ;)

---

### Post by Arutha on 2008-05-27
thank you, spiderbatdad :)

I didn't even know I have an "Imagemick Suite" installed on my Ubuntu... but it's great, works perfectly!

---

### Post by elgreengeeto on 2008-11-17
If you have images of different sizes, adding the option "-define pdf:use-trimbox=true" seems to allow the pages within the pdf to be different sizes too. I had some pictures in landscape and some in portrait and wanted to maintain that without distortion in my pdf, so this did the trick:

> convert -define pdf:use-trimbox=true *.JPG new_pdf.pdf

Refer to ImageMagick [formats page]("http://www.imagemagick.org/www/formats.html").

Note you can do [lots of other things]("http://www.imagemagick.org/script/command-line-options.php#resize") too with convert, like resizing each image:

> convert -resize 1500x1500 -define pdf:use-trimbox=true *.JPG new_pdf.pdf

---

### Post by ubunutucyclotron on 2010-05-21
Awesome! Thanks Spiderbatdad and co :)

---

### Post by Paddy Landau on 2010-05-21
> **Arutha said:**
> When I connect my camera, is F-Spot really the only way to copy my photos? Can't I just browse the camera like a mass storage device? Or mount it somehow? (I have a FujiFilm F31fd).
When you attach your camera, it automatically mounts as a mass storage device.

Your settings say that if it's a camera, then load F-Spot automatically. If you don't like that, you can simply close F-Spot and then browse your mounted camera as a normal mass storage device.

On my system (Hardy), I can set the default to not open F-Spot at all. However, on Lucid, I cannot find that same setting.

---

