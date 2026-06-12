---
title: "labeling images -- general advice"
date: 2007-09-16
forum: Programming Talk
---

### Post by nitro_n2o on 2007-09-16
hi all, 
i need some general advice/direction on this. 
I want to be able to draw boxes on images to label some features, say faces, so that i can tell exactly the position of a face in a photo.. 
Any ideas on how can i do this? perhaps a package or something like that.. but lets not do it in Java 
 
is openCV capable of doing something like this? or imagemagick?

thx

---

### Post by cwaldbieser on 2007-09-16
> **nitro_n2o said:**
> hi all, 
i need some general advice/direction on this. 
I want to be able to draw boxes on images to label some features, say faces, so that i can tell exactly the position of a face in a photo.. 
Any ideas on how can i do this? perhaps a package or something like that.. but lets not do it in Java 
 
is openCV capable of doing something like this? or imagemagick?

thx

ImageMagick can certainly draw on existing images.  If you are asking if it can identify specific parts of a photo to be labeled, it cannot do that.

---

### Post by nitro_n2o on 2007-09-16
sorry if my question wasn't clear enough 
i want to be able to draw boxes on pictures using the mouse and then get the coordinates of the box i've just drawn 

something like an object marker.. 

thx, any help is appreciated

---

### Post by cwaldbieser on 2007-09-16
> **nitro_n2o said:**
> sorry if my question wasn't clear enough 
i want to be able to draw boxes on pictures using the mouse and then get the coordinates of the box i've just drawn 

something like an object marker.. 

thx, any help is appreciated

You could do this using Tkinter and python (the canvas widget would let you do it pretty easilly).  Other GUI toolboxes probably have something similar (QT, wxWidgets, etc.).

The ImageMagic command line tools are more useful for making non-interactive changes to image files.  It does include GUI tools, but these seem like they are geared more for experimenting with how certain commands work.

---

### Post by gnusci on 2007-09-17
I recommend you use OpenCV:

[http://sourceforge.net/projects/opencvlibrary/](http://sourceforge.net/projects/opencvlibrary/)
[http://opencvlibrary.sourceforge.net/](http://opencvlibrary.sourceforge.net/)
[http://en.wikipedia.org/wiki/OpenCV](http://en.wikipedia.org/wiki/OpenCV)
[http://www.cs.iit.edu/~agam/cs512/lect-notes/opencv-intro/index.html](http://www.cs.iit.edu/~agam/cs512/lect-notes/opencv-intro/index.html)

---

### Post by nitro_n2o on 2007-09-17
these are all general tutorials and docs about OpenCV, none of them has good detail about doing what i want to do, but thx anyways nice list

---

### Post by jniebles on 2007-12-13
it's probably too late, but this tool does what you want to do

[http://robotik.inflomatik.info/guides.html](http://robotik.inflomatik.info/guides.html)
[http://robotik.inflomatik.info/other/opencv/OpenCV_ObjectDetection_Demo.exe](http://robotik.inflomatik.info/other/opencv/OpenCV_ObjectDetection_Demo.exe)

it's compiled for windows, but it includes source code and I could run it under wine

---

