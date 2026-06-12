---
title: "QtCreator query about loading images"
date: 2009-06-08
forum: Programming Talk
---

### Post by mdurham on 2009-06-08
When loading an image using:
imageLabel->setPixmap(QPixmap::fromImage(image));
If image is (say) xxx.jpg, fromImage() fails.

The docs say:
> By default, Qt can read the following formats:

Format	Description
BMP	Windows Bitmap
GIF	Graphic Interchange Format (optional)
JPG	Joint Photographic Experts Group
JPEG	Joint Photographic Experts Group
MNG	Multiple-image Network Graphics
PNG	Portable Network Graphics
PBM	Portable Bitmap
PGM	Portable Graymap
PPM	Portable Pixmap
TIFF	Tagged Image File Format
XBM	X11 Bitmap
XPM	X11 Pixmap

But the only supported images, according to QImageReader::supportedImageFormats() are these:
> bmp
pbm
pgm
png
ppm
xbm
xpm

Help would be appreciated on what I must do to read in a jpg.
Cheers, Mike

---

