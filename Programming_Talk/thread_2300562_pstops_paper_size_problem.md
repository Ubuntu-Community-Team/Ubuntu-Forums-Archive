---
title: "pstops paper size problem"
date: 2015-10-26
forum: Programming Talk
---

### Post by zaitsev_cray on 2015-10-26
Hello. I'm new with Ubuntu.

I am encountering a problem with pstops. I'm trying to create a PDF in a 4-up style from a multipage pdf that has 4inx6in size. I wanted the postscript output to be a legal size when I use pstops, but after creating a pdf out of the postscript output, the size is always letter even though I clearly specified to use legal.

Here is the content of the sh file

> pdf2ps test.pdf CombinedPDF.ps
pstops -q -plegal 4:0\(4.3in,4.5in\)+1\(0.15in,4.5in\)+2\(4.3in,-2.7in\)+3\(0.15in,-2.7in\) CombinedPDF.ps CombUPSUCC.ps
ps2pdf CombUPSUCC.ps sample.pdf
rm CombUPSUCC.ps CombinedPDF.ps 


Can anyone help me. I'm new with this. Thanks

---

