---
title: "problems compiling in Kile"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by wonderingwhy on 2008-08-21
I'm not particularly new LaTeX but I am new to Ubuntu and Linux.  I was unsing TeXnic Center on Windows.

I've taken my tex file which I know is properly coded and am trying to run it through kile.  I get the following message:


[COLOR="Purple"][PDFLaTeX] testing.tex => testing.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./testing.tex:19:File `apacite.sty' not found. ^^M
[PDFLaTeX] 1 error, 0 warnings, 0 badboxes

[ViewPDF] The file /home/phil/Documents/LaTeX file depository/testing.pdf does not exist; did you compile the source file?[/COLOR]

In TeXnic center I also got the `apacite.sty' error message but it never affected the pdf out put, ever. 

[COLOR="Purple"][ViewPDF] The file /home/phil/Documents/LaTeX file depository/testing.pdf does not exist; did you compile the source file?[/COLOR]

I think the above is the real issue.

Is this a Kile issue or a Ubuntu issue both or neither?

Thanks

---

### Post by Pro-reason on 2008-08-21
By default, Kile will compile as a DVI.  Make sure you compile as a PDF if you want to view it as a PDF.  Alternatively, view the DVI.

Kile just uses the underlying LaTeX system.  You ought to simply go to the command line and compile your LaTeX source to see if it works.  Only if Kile fails but the command line works will you know that it is a Kile problem.

---

### Post by wonderingwhy on 2008-08-21
Thanks, tried that and got more of the same, I'll try a Kile/LaTeX Forum.

Thanks again, much appreciate your time.

---

### Post by Pro-reason on 2008-08-21
> **wonderingwhy said:**
> Thanks, tried that and got more of the same, I'll try a Kile/LaTeX Forum.

Thanks again, much appreciate your time.

Try [http://groups.google.com/group/comp.text.tex](http://groups.google.com/group/comp.text.tex)

Or perhaps you could post here the exact output that you get when you type “pdflatex NAMEOFYOURFILE.tex”.

---

### Post by wonderingwhy on 2008-08-22
I sorted it by down loading apacite via synaptic.  Now I have no problems compiling at all.  Being a nubie to ubuntu, I didn't realise about synaptic. 

Thanks for the help - mucho appreciated.

---

### Post by dvase on 2008-08-26
> **wonderingwhy said:**
> I sorted it by down loading apacite via synaptic.  Now I have no problems compiling at all.  Being a nubie to ubuntu, I didn't realise about synaptic. 


FYI: In addition to synaptic, there is a command line version of MiKTeX utilities available at [http://miktex.org/unx/Default.aspx](http://miktex.org/unx/Default.aspx).  It does involve compiling the source.

---

