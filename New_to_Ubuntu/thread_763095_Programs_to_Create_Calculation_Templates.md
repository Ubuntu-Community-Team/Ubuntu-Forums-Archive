---
title: "Programs to Create Calculation Templates"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Gripp on 2008-04-22
i'm looking for a linux program similar to Mathcad. 
something that will show inline equations and perform the math based on predefines variables.  even more i would like it to be able to show/hide entire sections.  or maybe select what calculation are to be performed based on the information provided

it seems like LaTeX might be a good choice, only i'm not quite understanding how to get it actually perform the calculations, and i dont really like the idea of having to program everything (i'm not a programmer...)

---

### Post by polmir on 2008-04-22
> **Gripp said:**
> 
...
it seems like LaTeX might be a good choice, only i'm not quite understanding how to get it actually perform the calculations, and i dont really like the idea of having to program everything (i'm not a programmer...)
Latex is very simply.
[ftp://ftp.gust.org.pl/TeX/info/lshort/english/lshort.pdf]("ftp://ftp.gust.org.pl/TeX/info/lshort/english/lshort.pdf")
[http://www.tug.org/texlive/doc.html]("http://www.tug.org/texlive/doc.html")
[http://www.tug.org/texlive/]("http://www.tug.org/texlive/")
[http://www.tug.org/texlive/doc/texlive-en/live.html]("http://www.tug.org/texlive/doc/texlive-en/live.html")

Try lyx:
> LyX is an almost WYSIWYG-frontend for LaTeX that runs under the X Window System. It makes the power and typesetting quality of LaTeX available for people who are used to word processors.

```
sudo apt-get install lyx
```

---

### Post by CalcTeX on 2009-10-22
For calculations in LaTeX you can use a CalcTeX package. You can creating a templtates within hiding parts too. For example:
```

this is text... and definition of a value $a:=\pi/2$ next
is possible to print a value $a$ and def. b value \[b:=sin(a)\]

``` 
Is possible creating calculations within units too.
For more info pls visit project's web [http://sg.bzip.pl/CalcTeX]("http://sg.bzip.pl/CalcTeX")
I'm author of this package and I'm ofen for help you.

---

