---
title: "Converting PDFs to Grayscale"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by Partizan242 on 2011-11-25
The Ubuntu community has helped me a lot, so now I'm going to add some help for others. 

I'm a beginner and I was having difficulty printing my PDF files in grayscale. I felt like I did every trick in the book to do it and nothing was working. So I tried to convert the pdf to grayscale and that was tough too. There were threads telling me to do imagemagick-this and ghostscript-that and I was still lost. Then I found this trick somewhere on the web:

(my color pdf is called Napoleon.pdf)

1. Make a copy of the pdf to convert on the desktop.

2. Open a terminal with Applications->Accessories->Terminal

3. type: cd Desktop

4. type: pdf2ps -sDEVICE=psgray Napoleon.pdf   
[substitute "Napoleon.pdf" for the name of your file. A .ps file was created on your desktop]

5. type: ps2pdf Napoleon.ps 
[again, substitute Napoleon.ps for the name of the ps file on your desktop.]

And voila! That pdf copy on the desktop is now a nice looking file in grayscale. Print away or do what you want to do with it.

I hope this thread helps at least one person out there who wanted to convert a pdf to grayscale but was having trouble.

PS And if what I did actually WAS imagemagick or ghostscript, then cool.

---

### Post by llamabr on 2011-11-25
imagemagick will do the same trick, but yours works too, obviously.

pdf2ps and ps2pdf don't use imagemagick, they use gs, which uses ghostscript.  In fact, they're both just short scripts which call ps.  You can look at the code by opening them with a text editor:

```
nano /usr/bin/pdf2ps
```

and 

```
nano /usr/bin/ps2pdf
```

---

