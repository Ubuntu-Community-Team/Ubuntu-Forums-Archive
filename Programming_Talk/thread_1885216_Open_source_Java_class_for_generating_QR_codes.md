---
title: "Open source Java class for generating QR codes"
date: 2011-11-22
forum: Programming Talk
---

### Post by tornadof3 on 2011-11-22
Hello. There are several Java classes for generating QR codes, but none that appear to be open source, easily available etc.. Can anyone point me in the right direction, I would like to be able to easily generate QR codes and don't quite feel up to writing my own class to handle this.

Thanks

---

### Post by An Sanct on 2011-11-22
[http://www.onbarcode.com/products/java_barcode/barcodes/qrcode.html](http://www.onbarcode.com/products/java_barcode/barcodes/qrcode.html)

---

### Post by tornadof3 on 2011-11-23
Hmm, this looks interesting although it seems closed-source and must be purchased to use, unless I am missing something?

---

### Post by An Sanct on 2011-11-23
> **tornadof3 said:**
> Hmm, this looks interesting although it seems closed-source and must be purchased to use, unless I am missing something?

Oh :) I didn't go that deep into the source ... sorry.

Google charts support qr codes as of may 2009 - look [here]("http://www.google.com/codesearch#search&q=qr+package:http://charts4j%5C.googlecode%5C.com") and the [API wiki]("http://en.wikipedia.org/wiki/Google_Chart_API")

You should also take a look at this repo - [d-project]("http://d-project.googlecode.com/svn/trunk/misc/qrcode/") the link is to a folder, where different language qr code generators are...

EDIT: there are direct download links [here]("http://code.google.com/p/d-project/") and the JAVA one is [here]("http://d-project.googlecode.com/files/qrcode-java.zip")
(I also noticed, that the answer to this question could provide me with up to [250$]("http://www.freelancer.com/projects/PHP-Website-Design/Code-Generator-with-Stats.1271000.html") :))

---

### Post by fct on 2011-11-25
I heartily suggest zxing:

[http://code.google.com/p/zxing/](http://code.google.com/p/zxing/)

Apart from a variety of barcode generators, it includes barcode readers which we have successfully used at work.

Hope it helps.

---

### Post by tornadof3 on 2011-11-25
Zxing looks like it will do exactly what I need. Thank you to everyone for their responses.

---

