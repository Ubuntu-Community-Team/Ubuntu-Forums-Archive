---
title: "TeX packages"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by hmiersch on 2015-02-01
hi

the other day i moved my TeX projects to my new ubuntu HD. then i tried to typeset one of them using TeXstudio and it gave me an error message, saying that it couldn't find the glossary package. so now the question is, how can i install that package?

---

### Post by mJayk on 2015-02-01
[http://www.maxmanders.co.uk/2012/01/05/missing-ubuntulatex-glossaries.html](http://www.maxmanders.co.uk/2012/01/05/missing-ubuntulatex-glossaries.html)

---

### Post by Impavidus on 2015-02-01
The glossaries package is included in **texlive-latex-extra** on Ubuntu 14.04 and I believe on 12.04 too, but I think it's no longer in the repositories on 14.10. And glossaries has seen a large number of improvements recently, so you may prefer the latest version anyway. I installed the latest version manually a few months back to get rid of a bug which I had reported myself. Download the files from [CTAN]("http://ctan.org/tex-archive/macros/latex/contrib/glossaries") and install them in /usr/local/share/texmf (except the makeglossaries perl script, which belongs in /usr/local/bin/). You may need some dependencies. So if you get an error, read the error message. It mentions the missing package. Then go to CTAN again and download and install the dependencies, until you get no more errors.

Note that the blogpost linked to by mJayk is three years old. The dependencies of the glossaries package have changed since then.

---

### Post by hmiersch on 2015-02-06
ok, i've managed to install the glossaries package. but in order to make changes appear, i have to go to the terminal and use makeglossaries. is there a way to make texstudio do that automatically?

---

### Post by Impavidus on 2015-02-06
I think so, by properly [configuring the build system](http://texstudio.sourceforge.net/manual/current/usermanual_en.html#SECTION02a). But I don't use texstudio myself, so I can't help with that.

---

### Post by hmiersch on 2015-02-07
i switched from pdflatex to latexmk, and at first i thought that did the trick but apparently not. time to visit that link again...

---

