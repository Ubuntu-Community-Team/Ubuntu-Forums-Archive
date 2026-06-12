---
title: "why does typography get ugly when I scale down bitmap image?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-17
Hello,
We have some images with text. When we shrink the image, the text looks really ugly. We would think that text becomes ugly only when enlarging images. Please help.

---

### Post by SeijiSensei on 2012-04-17
Reducing the size of a bitmap image means replacing groups of pixels with larger ones that are averages of the ones being replaced.  Those averages may not look as good as the originals.  In addition, good fonts also include "anti-aliasing" adjustments which handles how things like curves and corners are reproduced by square pixels.  

If the graphics were created with a vector format like PNG rather than bitmaps, they would scale better.  Bitmaps are really a poor choice for anything that needs to be resized.

You might try installing Imagemagick ("sudo apt-get install imagemagick") to convert the bitmaps to PNG and see if they scale any better. I'm not promising anything, though.  The scaled PNGs might also be ugly since they'll have, at best, the same resolution as the original bitmaps.

---

### Post by hanzj on 2012-04-17
Aren't PNGs bitmaps, and not vector?

---

### Post by SeijiSensei on 2012-04-17
Oops, sorry, yes it is.  From [http://www.libpng.org/pub/png/pngintro.html](http://www.libpng.org/pub/png/pngintro.html)

"Like GIF and TIFF, PNG is a raster format, which is to say, it represents an image as a two-dimensional array of colored dots (pixels). PNG is explicitly not a vector format, i.e., one that can store shapes (lines, boxes, ellipses, etc.) and be scaled arbitrarily without any loss of quality (generally speaking). For that you probably want SVG or PostScript."

Imagemagick [supports]("http://www.imagemagick.org/script/formats.php") conversion to Postscript and to SVG, though with the caveat that "SVG is a complex specification and support for the specification in ImageMagick is not complete."

---

