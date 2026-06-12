---
title: "ImageMagick gaussianBlur?!"
date: 2013-12-26
forum: Programming Talk
---

### Post by fallenshadow on 2013-12-26
Hey all,

Does anyone know why imageMagick gaussianBlur does this to the image?? O_O

[IMG]http://i39.tinypic.com/1zvsxoo.jpg[/IMG]

gaussianBlur(0.0, 1.0);

Values passed to it: (const double width_, const double sigma_)

---

### Post by ofnuts on 2013-12-26
Looks more like gaussian RGB noise to me.

---

### Post by Unterseeboot_234 on 2014-01-01
I think your seeded values are too tight. The 'rosettas' are the width of half of the period character when ideally we need the buffered digital grid at least 4 pixels by 4 pixels. I see where you are using the C++ wrappers for ImageMagick. The doubles arguments should accept a decimal without the fraction.

I like the combination of perl / EXIFtool / lib_imagemagick as a folder full of useful scripts, but...
Using the lib_imagemagick from Terminal. 

[FONT=Fixedsys]user@user-AMD64Athlon:~/Desktop/umagemag_test$ convert IMG_6858.JPG -blur 0x5 img_blur.jpg
user@user-AMD64Athlon:~/Desktop/umagemag_test$ convert IMG_6858.JPG -filter Gaussian -blur 0x8 img_gaus.jpg[/FONT]

The Gaussian filter appears to preserve the histogram of the image as a smoother curve.

---

