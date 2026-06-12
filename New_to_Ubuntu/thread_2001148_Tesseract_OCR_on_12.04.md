---
title: "Tesseract OCR on 12.04?"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by wisdomlight on 2012-06-10
Hi,
Can any one explain how to work with the Tesseract OCR ?
It has no GUI as far as I can see,[OCRFeed does not work].
I read that tesseract is great program but have no clue how to run it?
As far as I can tell it is installed on my ubuntu.

Any suggestion for a complete beginner will be helpful.

Thanks

---

### Post by forrestcupp on 2012-06-10
As far as I know, you have to use Tesseract from within another program. I use gscan2pdf, which is in the repos. In gscan2pdf's OCR settings, just set it to use Tesseract.

---

### Post by Irihapeti on 2012-06-10
You can use tesseract as a stand-alone program.

The basic command for tesseract is:

```
tesseract inputfilename outputfile
```

Input file can be in a number of formats - I've used .png and .tif (uncompressed). Output file will be text.

Traditionally, tesseract didn't handle multi-column originals and other fancy layouts. You may be able to do that with some of the options which are set out in the man page (man tesseract).

---

### Post by coffeecat on 2012-06-10
Useful community documentation here:

[https://help.ubuntu.com/community/OCR#Tesseract](https://help.ubuntu.com/community/OCR#Tesseract)

One quirk is that input TIFs must have a .tif extension, not .tiff.

---

### Post by Nalin x Linux on 2012-11-12
Linux-intelligent-ocr-solution

[http://code.google.com/p/linux-intel...-ocr-solution/](http://code.google.com/p/linux-intel...-ocr-solution/)

Lios is a free and open source software for converting print in to text using either scanner or a camera, It can also produce text out of scanned images from other sources such as Pdf, Image or Folder containing Images. Program is given total accessibility for visually impaired. Lios is written in python, and we release it under GPL3 license. Lios will work with Debian based operating systems. There are great many possibilities for this program, Feedback is the key to it

---

