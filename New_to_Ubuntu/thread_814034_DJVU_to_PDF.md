---
title: "DJVU to PDF"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Sordelka on 2008-05-31
Is there a way to convert djvu to pdf in ubuntu?

---

### Post by kwacka on 2008-05-31
DJview4 can export as PDF.

Its in the universe repository.

---

### Post by Ripfox on 2008-05-31
There seems to be a solution here: [http://ubuntuforums.org/showthread.php?t=216531](http://ubuntuforums.org/showthread.php?t=216531)

Let me know if it works


Rip

---

### Post by Sordelka on 2008-05-31
Ripfox

I am currently converting from ps to pdf, hope it works :-)

---

### Post by Ripfox on 2008-05-31
I am interested to know if this method worked?

---

### Post by kwacka on 2008-05-31
Opening ```
djview ./Elektor.djvu
```

opens the file in a GUI, and clicking on File --> Export does produce Elektor.pdf

---

### Post by ziri on 2009-01-08
ddjvu -format=pdf file.djvu file.pdf

---

### Post by ziri on 2009-01-08
Unfortunately, all the mentioned methods store only the image data in the PDF. If you want also the text, install the PDF printer (cups-pdf), open the document in djview and print it to the PDF printer.

---

