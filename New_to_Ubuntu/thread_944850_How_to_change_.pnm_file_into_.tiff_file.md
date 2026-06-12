---
title: "How to change .pnm file into .tiff file"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-10-11
I have a single column of text from a book page scanned and saved as a pnm image. I want ultimately to use tesseract to turn the image into editable text. But, as I understand it, I must first save the pnm image as a .tiff file. However when I try to do that I receive this message: 

Eye of GNOME could not determine a supported writable file format based on the filename.

Please try a different file extension like .png or .jpg.

What do I need to do to be able to create .tiff files? I am using Ubuntu 8.10.

---

### Post by BandD on 2008-10-11
Try using GIMP.  It should be in Applications --> Graphics.  Or you should be able to right click on the saved pnm file, choose open with, then select GIMP.  It'll open up  Then go to File --> Save As, figure out where you want to save it, then typ the name of the file with a .tiff after it (i.e. ubuntu.tiff)  That should do the trick.

---

### Post by The Cog on 2008-10-11
Look at imagemagick. It's command line, but I gather there are GUI front ends it you feel the need.

Doh! Or the GIMP if course.

---

### Post by Patb on 2008-10-11
Ludwig, you could use Gimp to open the file and save as tiff. I also like a smaller program which handles many different graphics formats, Xnview. It is in the normal repositories.

Hope this helps. Cheers, Pat.

---

### Post by Ludwig9 on 2008-10-12
> **BandD said:**
> Try using GIMP.  It should be in Applications --> Graphics.  Or you should be able to right click on the saved pnm file, choose open with, then select GIMP.  It'll open up  Then go to File --> Save As, figure out where you want to save it, then typ the name of the file with a .tiff after it (i.e. ubuntu.tiff)  That should do the trick.
I right clicked on the file and saved it, etc. Success! Thanks to all.

---

### Post by Ludwig9 on 2008-10-12
I have gone into Synaptic Package Manager and in Graphics (universe) installed tesseract-ocr (2.03-2) and tesseract-eng (2.00.1) as well as tesseract for several other languages. I have then gone to Terminal and given it some commands with the following results:

> george@george-desktop:~$ tesseract test10.tif test10 -1

Could not open file, -1

george@george-desktop:~$ tesseract test10.tif test10 -2

Could not open file, -2

george@george-desktop:~$ tesseract test10.tif test10

Tesseract Open Source OCR Engine

TIFFOpen: test10.tif: Cannot open.

tesseract:Error:Read of file failed:test10.tif

Signal_exit 31 ABORT. LocCode: 3  AbortCode: 3

george@george-desktop:~$ 

 

Have I given it the right commands? As you see, I changed -1 to -2 and then left -1 out altogether. Does it make any difference whether the input file is .tif or .tiff?
I have never used Tesseract before and perhaps simply don't know how to use it, but can the problem be that tesseract simply is not able to read the text of the .tif file. As I said before, the page is from an old book. The text, although quite readable, is written in an italicized font, and the print quality is hardly perfect.

---

### Post by kwacka on 2008-10-12
Try using the lower case letter 'L' (for 'language') instead of the numeral one, i.e. l instead of 1

e.g. tesseract test10.tif test10 -l eng

will produce a file 'test10.txt in English ('-l deu' for German, etc)

(BTW, it's usually better to start a new thread if you ask a new question - it's less likely to get over-looked)

---

### Post by Ludwig9 on 2008-10-12
> **kwacka said:**
> Try using the lower case letter 'L' (for 'language') instead of the numeral one, i.e. l instead of 1

e.g. tesseract test10.tif test10 -l eng

will produce a file 'test10.txt in English ('-l deu' for German, etc)

(BTW, it's usually better to start a new thread if you ask a new question - it's less likely to get over-looked)

Ok, I will start a new thread. I tried what you suggested and got this result. 
> george@george-desktop:~$ tesseract test10.tif test10 -l eng
Tesseract Open Source OCR Engine
TIFFOpen: test10.tif: Cannot open.
tesseract:Error:Read of file failed:test10.tif
Signal_exit 31 ABORT. LocCode: 3  AbortCode: 3
george@george-desktop:~$ 



---

