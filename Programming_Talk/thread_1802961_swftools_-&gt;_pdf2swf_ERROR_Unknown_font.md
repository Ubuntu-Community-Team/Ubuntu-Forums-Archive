---
title: "swftools -&gt; pdf2swf ERROR Unknown font"
date: 2011-07-12
forum: Programming Talk
---

### Post by lion69 on 2011-07-12
hi all
i am trying to convert pdf to swf. and i want that each page convert in one swf file. when i convert whole document to one swf file everything is fine. but when i try to convert each page to one file i get an erron and of course the text in swf file is a set of chars. 
error:
```
WARNING swf_drawchar: Font is NULL
ERROR  Unknown font id: NABUUW+TimesNewRomanPSMT-217-0
```
i try to connect fonts but it does't work:
```

pdf2swf 2.pdf -p 12-14 -o %.swf -F usr/local/share/swftools/fonts 

pdf2swf 2.pdf -p 12-14 -f home/lion69/t/fonts/TimesNewRomanPSMT.otf -o %.swf

pdf2swf 2.pdf -p 12-14 -o %.swf --fontdir=/home/lion69/t/fonts


```
xpdf lib is installed.
please help me.

---

