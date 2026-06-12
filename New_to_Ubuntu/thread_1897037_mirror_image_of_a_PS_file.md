---
title: "mirror image of a PS file"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by belura on 2011-12-18
:pI want to get mirror image of a PS file for printing purpose. In debian I could use dvips -o -F -h rev.pro file.ps to get this done. But I find that does not work in Ubuntu. What is the other way?

---

### Post by sudodus on 2011-12-18
dvips is included in ubuntu (at least in the repositories). I look in the manual and find
```
       -F     Causes Control-D (ASCII code 4) to be appended as the very  last
              character  of the PostScript file.  This is useful when dvips is
              driving the  printer  directly  instead  of  working  through  a
              spooler,  as is common on extremely small systems.  NOTE! DO NOT
              USE THIS OPTION!

``` Maybe you should try it without the -F option

*Edit:* I think that you can make an image file and use the gnu image processing tool ***gimp*** which is a good tool for many image processing operations. If you want to process a batch, install ***ImageMagick*** read the tutorials on the internet, and use its tools from the command line.

---

### Post by belura on 2011-12-18
It has nothing to do with dvips the problem is the header rev.pro and the reply I get is that the header rev.pro is not found. I do not know where to look for it

---

### Post by sudodus on 2011-12-18
Then I suggest that you use ***pstopnm*** to convert fron ps to pnm file format. A pnm file can be processed by gimp or (from imagemagick) convert.
```
convert -flip # or
convert -flop 
``` should do the job.

---

