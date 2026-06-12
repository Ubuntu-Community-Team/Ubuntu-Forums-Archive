---
title: "pdf opening in Evince and Kpdf but not in Adobe Reader"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-06-24
Here is a test pdf which I made by my self which opens in Evince and Kpdf instantaneously but not in Adobe Reader. Any suggestion how to open it in Adobe Reader because I have to sent it someone who is using Windows and he is not able to Read some similar kind of pdf that I have attached.

---

### Post by HereInOz on 2008-06-24
Find yourself a pdf file in nautilus, then right click on it, and then click properties.  

One of the tabs in the properties box which opens up will be "Open with"

Click on that tab and you should be presented with the option to select either evince or acrobat reader as the default "opener" for all files of that type.

---

### Post by _sphinx_ on 2008-06-24
I think you didn't got me, I am saying that the attached pdf opens with evince, and I have no problem with it. But when I am trying to open it with Adobe Reader 8 it gives me the error message```
There was a error processing this page. There was a problem reading this document
```. I will suggest please try to open the attached pdf with your adobe reader and see if this opens.

---

### Post by _sphinx_ on 2008-06-24
Also I am using imagemagick to convert png to this pdf.

---

### Post by _sphinx_ on 2008-06-25
Finally I was able to make a pdf of a png image. But I have to write a latex script and insert the image through the script.
Also I will not mark this thread sloved since, I am still confused as to why the pdf made by imagemagick is not able to open in Adobe Reader.

---

### Post by muadnu on 2008-07-29
Just to add my experience... I've had trouble with files created with latex in Adobe Reader which are read perfectly with Evince/xpdf/kpdf (same error _sphinx_ mentions). The problems in my case usually come from using beamer though. But in any case, there definitely is something in Adobe Reader (maybe just in version 8) which is causing trouble with files created, is seems like, in Linux, which I find weird.

---

### Post by polmir on 2008-08-02
This is not a valid document by the end of pdf.
Compare with any editor (eg vim) a pdf file from the Adobe Reader, which reads.
Try OpenOffice to comply with pdf files or Latex.

---

