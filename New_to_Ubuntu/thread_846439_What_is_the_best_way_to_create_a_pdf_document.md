---
title: "What is the best way to create a pdf document"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by gatorbrit on 2008-07-01
I made a document in OO writer and when I did 
->EXPORT to PDF 
some of the fonts were a little messed up.

So I tried printing to file and I ended up with a PS file not a PDF.

How can I create a pdf using print to file in linux?

(in windows I can do it - but I have adobe acrobat installed).


Thanks

Rich

---

### Post by bluepowder7 on 2008-07-01
what fonts are you using?  do you have the right fonts installed, or is it picking the closest similar font?

sudo aptitude install msttcorefonts

(or something like that)

---

### Post by gatorbrit on 2008-07-01
I'll check that.  Actually it printed nearly all the page numbers right, except a few that seemed to be greek or arabic.  Very strange - and not consistent either.  Thats why I wanted to print directly to the pdf.

---

### Post by tchu on 2008-08-30
Maybe try what I have written here (post no. 2):
[http://ubuntuforums.org/showthread.php?t=881853](http://ubuntuforums.org/showthread.php?t=881853)

Good luck!

---

### Post by swoll1980 on 2008-08-30
ctrl+p select pdf as your printer, click print, instead of printing to paper it will create a pdf file

---

### Post by gmxgeek on 2008-08-30
OO has always worked perfectly for me, no matter what i gave as input

---

