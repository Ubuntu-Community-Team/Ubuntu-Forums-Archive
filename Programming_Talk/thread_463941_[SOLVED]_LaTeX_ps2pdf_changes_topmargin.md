---
title: "[SOLVED] LaTeX: ps2pdf changes topmargin"
date: 2007-06-04
forum: Programming Talk
---

### Post by tjansson on 2007-06-04
I don't know if this is really a programming question but I hope you can help af anyway. I have this ps document which I am converting with ps2pdf to a pdf document. The problem is that the PDF have other topmargins that the ps file. 

In the ps file I have something like 2,5cm topmargin and 3cm bottommargin but in the pdf file the topmargin is 2,5cm and 4,5 cm bottommargin. The page has been contracted and is not centeret anymore. 

Does anybody know why this happen or how to fix it? Is there a way to change top and bottommargin of pdf already created?

---

### Post by tjansson on 2007-06-10
I found the solution: 
```
ps2pdf -sPAPERSIZE=a4 foo.ps foo.pdf

```

---

