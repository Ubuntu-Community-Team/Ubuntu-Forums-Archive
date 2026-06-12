---
title: "png to pdf conversion with imagemagick"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by inlinesidekick on 2012-04-25
I have a mix of .png and .pdf files. I am trying to use imagemagick to convert the png's to pdf's and then pyPdf to creat pdf portfolio of ~500 pdf's per portfolio. 
I am running 
convert trail_map.png trail_map.pdf 

and getting the following errors:
convert: no decode delegate for this image format `trail_map.png' @ error/constitute.c/ReadImage/544.
convert: missing an image filename `trail_map.pdf' @ error/convert.c/ConvertImageCommand/3017.

Does anybody know what this means?
Thanks!

---

### Post by cmont899 on 2012-04-25
Run the following to see if you have png support in imagemagick and libpng installed:

identify -list format | grep -i png
dpkg --search libpng

Are you able to convert to another file format first? png->jpg->pdf

---

### Post by inlinesidekick on 2012-04-25
I ended up having to install libpng and reinstall imagemagick and it all worked.
Thanks a lot!

---

