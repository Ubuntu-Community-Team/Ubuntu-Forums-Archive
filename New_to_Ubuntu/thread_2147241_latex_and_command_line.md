---
title: "latex and command line"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Lounis on 2013-05-21
Dear all,

first of all, I apologize if this is not the right place to ask my question. I am new in this forum.
I am trying to learn how to run a number of applications from the command line to get familiar with it. Latex is one of those programs. I managed to run it in the command line using "pdflatex myfile.tex" and it works perfectly. I would like to know if there is an option of pdflatex function that allows to display a preview of the pdf result right after the compilation (so that the pdf/dvi result opens automatically) ?

Thanks a lot.

---

### Post by Impavidus on 2013-05-21
```
pdflatex yourfile.tex && your_favorite_pdfreader yourfile.pdf
```
But I prefer to keep my .dvi files open in xdvi and have it reload automatically after each run of latex.
```
xdvi myfile.dvi &
latex myfile.tex #as often as I want
```

---

### Post by Lounis on 2013-05-28
Thanks Impavidus for your help,

Sorry for the late answer.

L.

---

### Post by marianoa on 2013-05-28
You can use latexmk, it compiles automatically the tex file when it's needed, for example when you modify the tex file or any file it depends on (figures, bibliography files etc.) and it also has the option to open the pdf viewer and update the pdf when changes are made. If you have a tex distribution installed you should also have latexmk and you can invoke it like this 
```
latexmk -pdf -pvc your_file.tex
```

the option "-pdf" is to compile using pdflatex and the option "-pvc" is to start a continuous preview of the produced pdf file. You can read more here [URL="http://http://www.ctan.org/pkg/latexmk/"]
http://www.ctan.org/pkg/latexmk/[/URL]

---

### Post by Lounis on 2013-05-28
Thank you Marianoa,

Thanks for your reply.

I tried your commands but it didn't work, I get this message in the terminal :

________________________________________________________

Latexmk: This is Latexmk, John Collins, 7 May 2011, version: 4.24.
**** Report bugs etc to John Collins <collins at phys.psu.edu>. ****
Viewing pdf
Latexmk: All targets (elcvia209.pdf) are up-to-date
Latexmk: I have not found a previewer that is already running. 
   So I will start it for 'elcvia209.pdf'
------------
For rule 'view', running '&if_source(  )' ...
------------
Running 'start xpdf  "elcvia209.pdf"'
------------

=== Watching for updated files. Use ctrl/C to stop ...
Syntax Error: Couldn't create a font for 'RTDCSO+NimbusRomNo9L-ReguItal'
Syntax Error: Couldn't create a font for 'ATNPAF+NimbusRomNo9L-Medi'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'FRNIHB+CMSY8'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'UUDSQA+CMR8'
Syntax Error: Couldn't create a font for 'SDVCAT+CMSY7'
Syntax Error: Couldn't create a font for 'RTDCSO+NimbusRomNo9L-ReguItal'
Syntax Error: Couldn't create a font for 'ZEWWSJ+CMR7'
Syntax Error: Couldn't create a font for 'RTDCSO+NimbusRomNo9L-ReguItal'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'ATNPAF+NimbusRomNo9L-Medi'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'RTDCSO+NimbusRomNo9L-ReguItal'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'ATNPAF+NimbusRomNo9L-Medi'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'YJCLWH+CMMI9'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'YJCLWH+CMMI9'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'YJCLWH+CMMI9'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Syntax Error: Couldn't create a font for 'YJCLWH+CMMI9'
Syntax Error: Couldn't create a font for 'BMUKPT+NimbusRomNo9L-Regu'
Segmentation fault (core dumped)



Thank you for your help.

---

### Post by marianoa on 2013-05-28
It's strange, if you try to run
```

pdflatex yourfile.tex
evince yourfile.pdf

```
do you get any error?

I've seen that latexmk tries to use xpdf to open the pdf, that could give rise to the problem. To change this and make it use evince you should create a file called .latexmkrc in your home folder and put these 2 lines in it
```

$pdf_previewer = "start evince";
$pdf_update_method = 0;

```

---

