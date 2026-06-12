---
title: "Xsane scanning for multiple pdf"
date: 2019-08-22
forum: New to Ubuntu
---

### Post by itdxb1 on 2019-08-22
Dear Team,

Does any one know, how to use the bar code as a file name while scanning as a file and saving it as a single pdf.

Thanks

---

### Post by him610 on 2019-08-22
You might want to take a look here, [https://www.gnu.org/software/barcode/]("https://www.gnu.org/software/barcode/")
It may help in your quest.

---

### Post by Holger_Gehrke on 2019-08-23
@him610: wrong direction ... GNU barcode generates barcodes; itdxb1 has a scanned barcode he wants decoded.

There is a library for decoding (some) barcodes (libzbar0) and a set of example programs (zbar-tools) which decodes barcodes either from image-files or from a v4l-device (webcams, ...). xsane AFAIK isn't set up to use this. 
So you could either 
- use the source code of xsane and change the program to give it that capability
or
- save the pdf to some temporary name and then run zbarimage on the pdf to decode the barcode and then rename the file.  This approach is made slightly difficult by the fact that zbarimage uses ImageMagick for reading and preprocessing the file and ImageMagick  is forbidden from working on pdf-files by a policy in /etc/ImageMagick-6/policy.xml. Enclosing the line '<policy domain="coder" rights="none" pattern="PDF" />' in an XML-comment ("<!-- ... -->") will fix that, but is risky if you're using the machine as a web-server and use ImageMagick in some web-application(s).

Holger

PS: Most barcodes just contain a number and you'd have to look up that number in some database / online-service to get something sensible from them (UPC, ISBN, ISSN).

---

