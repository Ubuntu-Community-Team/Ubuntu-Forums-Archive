---
title: "PDF to DOC Convertor for Ubuntu"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by anuraggautam on 2008-07-30
Hello,

Can anyone tell me how to convert PDF documents to DOC in Ubuntu Linux [Hardy Edition].

Please Ignore Wine , I want a solution which is for Linux not Windows dependent.

Regards

---

### Post by gjoellee on 2008-07-30
I think KOffice can open .pdf and save as .doc you can find it in Add/Remove

---

### Post by tackatucka on 2008-08-01
Well I would also like to convert pdf files into .doc, or even .txt files, without needing to install a whole office application.

I tried to find something  by using "apt-get search pdf | grep convert" but i just found packages which could convert into pdf files. KOffice might solve the problem but i really dont wanna install a full office-application only for converting files.

The question is if anybody knows any other application to solve this task?

Edit said I should go on exploring ubuntuforums and there it is xD

[how to convert pdftotext with pstotext]("http://ubuntuforums.org/showthread.php?t=702940&highlight=pdf+convert")

converting from text to doc shouldnt be a prob for you i guess ;)

---

### Post by Oerb on 2009-02-17
I use a Wine installation and pdf2html. It converts PDF to HTML which I then open in OpenOffice. Ok in OpenOffice 3.0 you could open PDF directly, but it is not in a good format to edit the Text.

---

### Post by lukjad on 2009-02-17
@anuraggautam
Just so you know, there are online converters that e-mail you the converted files. This may not be ideal if privacy is a big issue, but it's something to think about.

---

### Post by sahabcse on 2009-02-21
Hi 

Follow the URL 

=========================================
[http://sahabm.blogspot.com/2009/02/converting-pdf-to-doc.html](http://sahabm.blogspot.com/2009/02/converting-pdf-to-doc.html)
=========================================

Regards,
Sahab

---

### Post by sp176 on 2009-04-15
I use Okular

---

### Post by llamabr on 2009-04-15
This will often be more difficult than you're making it out to be.  

In the easy case, you can probably open your document in acroread or evince, and copy/paste to a txt file.  You'll find that openoffice 3.0 can make the conversion much easier for you (other apps will come along, but that the new oo can do it is kinda a big deal).  For cli, you can use pdf2ps > ps2txt.  But I find that this is not always very accurate.

Next, depending on how your pdf was made, it may get much more complicated.  Exporting a pdf from latex, oo, etc, embeds the fonts into the document.  If the document is made with a scanner, as is the case with many old journals and papers that you find in pdf form now, you need a much more specific (and expensive) piece of software, as they're often scanned as TIFF format.  You essentially need software that can recognize the shapes of the letters, and translate them into text.  Even the best (and most expensive) of these are not always very reliable.

For the first kind, I'd go with openoffice, even if it's a bit big for this project.  For the second, I've always given up when I did this research, because the software is too expensive for me (so I can't recommend one).

---

### Post by click4851 on 2009-04-15
yup, your headed into OCR software and that does get expensive....


but not always.....[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

---

### Post by gabak on 2010-11-26
do it with word from open office it works great !!!!!!!!!

---

### Post by Ivymin on 2011-10-26
Hi, my friend, i have read some article about pdf to word converter, you can have a try.
It can 
* Convert PDF to Word
* Choose whichever pages to be converted
* Convert any PDF document into MS Word document format (RTF or Word)

---

### Post by oldos2er on 2011-10-26
Closed, please do not bump old threads.

---

