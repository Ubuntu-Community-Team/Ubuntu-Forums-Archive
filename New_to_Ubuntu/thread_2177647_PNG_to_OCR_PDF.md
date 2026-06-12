---
title: "PNG to OCR PDF"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by PQcphx7 on 2013-09-29
Hello,

I am new at OCR.  Have the following goal(s):
1.  Saving PNG image file(s) of books from website (e.g. Google Books) to local PC (Ubuntu 12.04LTS 64-bit)
2.  Ultimately, maintain decent image quality of text on page.  Convert to PDF; add OCR for highlighting and search capabilities.  
3.  Combine pages into larger PDF (no problem using 'pdftk')

**My issue is with conversion of PNG to PDF with OCR.  I have tried:**

**Method 1:**
```
convert -monochrome -density 300 -normalize -depth 8 reader.png reader.pgm
tesseract -psm 1 reader.pgm output.pdf hocr
convert reader.pgm reader.jpg
hocr2pdf -i reader.jpg -s -0 readerFinal.pdf < output.pdf.html
```
* This partially works: image quality of page is worsened, and OCR is not very good.

**Method 2:**
open image in eog (Imager Viewer for Ubuntu)
write to PDF file
```
pdfsandwich -tesso -tesseract-config PDFfileFromEOG.pdf -o FinalOCRfile.pdf
```
* Quality of image is better; OCR is not so great.

There are a number of other means I have tried, without success.  I am missing something, but I am not sure what.

Here is an example page that I have attempted the above with:
[https://play.google.com/books/reader?id=KSVLAAAAYAAJ&printsec=frontcover&output=reader&authuser=0&hl=en&pg=GBS.PA59](https://play.google.com/books/reader?id=KSVLAAAAYAAJ&printsec=frontcover&output=reader&authuser=0&hl=en&pg=GBS.PA59)

It appears that I have an issue with quality of image, as well as tesseract ability to process (OCR).  Any help would be appreciated.

Thanks.

---

### Post by ajgreeny on 2013-09-29
Have you tried saving your original image files as .tif which in previous versions of tesseract was the only image type that worked? I use tesseract but have never OCR'd .png files, so I don't know if there is any problem about that file type, but I do use .jpg files without any problem and I get very good conversion.

One important thing to consider is the resolution of the image used; what resolution are you using when you OCR them to text? I hope they are not screenshots, as that will never be good enough for good OCR, normally being only 96dpi, when you need at least 300dpi in my opinion.

---

### Post by PQcphx7 on 2013-09-30
> **ajgreeny said:**
> Have you tried saving your original image files as .tif which in previous versions of tesseract was the only image type that worked? I use tesseract but have never OCR'd .png files, so I don't know if there is any problem about that file type, but I do use .jpg files without any problem and I get very good conversion.

One important thing to consider is the resolution of the image used; what resolution are you using when you OCR them to text? I hope they are not screenshots, as that will never be good enough for good OCR, normally being only 96dpi, when you need at least 300dpi in my opinion.


** Re: resolution **--> the PNG file automatically saved when one saves the complete webpage.  While the properties of the file indicate the image has 921x1456 pixels, I understand that this is meaningless.  So, I can't directly know what the resolution is. It is not a screen capture.  Using 'identify' and 'convert' I created various files with various densities, all of which indicate 921x1456 pixels (as expected).  I did notice, that if I use the 'monochrome' option, the letters get grainy.  However, if the appearance in the image viewer means anything, the quality of the original PNG file appears to be good (300 or better I presume, unless the image viewer, eog, is able to smooth/improve quality).  

If I assume that the PNG file resolution is 300 or better, what would the details of the .tif files (or .jpg files) that you convert be?  In other words, if I used 'convert' to convert the PNG file, what format details should I use?  (I am open to other conversion programs than 'convert'...)  What command line options do you use with tesseract? Do you use hocr2pdf as well, and options?

**Re: Method 1:** Perhaps the issue is the 'monochrome' option as well.  I had better success with the following (image quality appears same as original PNG file, OCR mush better / not perfect, but much better):
```
convert -density 600 -depth 8 reader.png reader.pgm
tesseract -psm 1 reader.pgm output.pgm.pdf hocr
convert reader.pgm reader.jpg
hocr2pdf -i reader.jpg -s -o readerDensity600Depth9pgmpng.pdf < output.pgm.pdf.html
```
So, perhaps the B&W conversion with 'monochrome' was the main issue. 

**Re: Method 2:** I was unable to make any progress via this method.  Attempts to use 'convert' to convert to *.tiff, then 'tiff2pdf' to convert to pdf, then 'pdfsandwich' - failed.  Attempted to convert *.tiff used in recent Method 1 above to *.pdf, then use pdfsandwich for OCR - failed:  output given below. 
```

>>~/Downloads/test/GB2$ convert readerCONVERT2.tiff readerCONVERT2TIFF-CONVERT2PDF.pdf

>>~/Downloads/test/GB2$ pdfsandwich -tesso /home/mcgrete/Downloads/tesseract-config 
readerCONVERT2TIFF-CONVERT2PDF.pdf -o readerCONVERT2TIFF-CONVERT2PDF-SANDWICHED.pdf
Input file: "readerCONVERT2TIFF-CONVERT2PDF.pdf"
Output file: "readerCONVERT2TIFF-CONVERT2PDF-SANDWICHED.pdf"
Number of pages in inputfile: 1
More threads than pages. Using 1 threads instead.
Processing page 1.
libpng error: No IDATs written into file
Error: /VMerror in --showpage--
VM status: 3 852294 2165352
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 9.05: Unrecoverable error, exit code 1
convert: Postscript delegate failed `readerCONVERT2TIFF-CONVERT2PDF.pdf':  @ error/pdf.c/ReadPDFImage/663.
convert: missing an image filename `png:/tmp/pdfsandwichaf253c.png' @ error/convert.c/ConvertImageCommand/3011.
sh: 1: cannot open /tmp/pdfsandwich086577.html: No such file
OCR done. Writing "readerCONVERT2TIFF-CONVERT2PDF-SANDWICHED.pdf"
```


FYI - I am using tesseract 3.02; pdfsandwich 0.0.8; hocr2pdf 0.8.5

If there are any suggestions on improving the OCR, I am open to it.  Here is the text that results from the OCR (Method 1 improvements as listed above...: See attached file outpu.pgm.pdf.html)
A lower resolution image of the page that was processed (small enought to upload) is attached too.  (Best perhaps to see the websitse if the link I provided works...)

Thanks!

---

