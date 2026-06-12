---
title: "Quick image resizing like MS-Paint?"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by mtrz2 on 2013-08-22
Hello,

I'm a less than a week Ubuntu user and i'm having a issue trying to complete an surely easy task: resize a simple JPEG image to shrink its size. Just for fb and forum postings.

In the -not so- old times i used to run MS-Paint, took me just about 15 seconds to do that.

In Ubuntu i just didn't find a app to do this: downloaded Gnome, Gimp and even Inkscape and nothing. The image viewers like "image viewer" and "ImageMagick" aparently doesn't have such possibility too.

Sorry to ask such a dumb question, i realy loved the design of Ubuntu and how smoothly it works, but some silly features didn seem to get yet.

Thanks a Lot.

M.

---

### Post by MartyBuntu on 2013-08-22
You can use this guide to install a right-click resize option:
[http://ubuntu-tips-tutorials.blogspot.ca/2012/10/quick-image-resize-on-ubuntu-right.html](http://ubuntu-tips-tutorials.blogspot.ca/2012/10/quick-image-resize-on-ubuntu-right.html)

---

### Post by Bachey on 2013-08-22
Mirage or Kolourpaint if you want something really similar to mspaint.

---

### Post by angry_johnnie on 2013-08-22
Using GIMP:

go to image > scale image

and change the image size as needed.


with imagemagick (which is a commandline tool, by the way):

```
cd /path/to/image
convert -resize 000x000 image.extension newimagename.extension
```

where 000x000 is the new size you want for it (like 1024x768 for example), and image.extension is the original filename and extension, and newimagename.extension is the new filename and extension.

keeping the same filename wil overwrite original file.


As far as I can remember, kolourpaint does have a resize option, although i'm not using KDE and i don't know it by heart.

---

### Post by mastablasta on 2013-08-23
Krita is another option.
Shotwell
Gwenview
gThumb

---

### Post by kurt18947 on 2013-08-23
I use GIMP for that. It may not be the fastest but once familiar it's fast enough for me.  My method is a two step process.  First load the image then image -> scale image -> pick a size - 800 X600 works pretty well for my purposes - click the 'scale' button.  Next go to File -> export -> rename if you want to keep the original image then click the 'export' button.  You'll be presented with a window where you can select the image quality.  Higher number=better quality/larger file size.  For most purposes 25 seems to work pretty well for me.

---

### Post by raja.genupula on 2013-08-23
+1 to command line tool. image magic can be installed by [INDENT]sudo apt-get install imagemagick



[http://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/](http://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/) 
[/INDENT]

---

### Post by aditya8892 on 2013-08-23
you can also use percentages with that :)

---

### Post by mtrz2 on 2013-08-24
Ok, people, Thanks a lot! Problem solved.

I did the instalation of that app that allows me resize by clicking with a right click in the image thumbnail.

Works a lot ;)

---

