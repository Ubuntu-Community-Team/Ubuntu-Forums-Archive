---
title: "Bibtex Issues"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by buntu_hugenewbie11 on 2008-06-10
I use Kile and Texlive.
For some reason I can't compile my bibtex.
I get: [BibTeX] finished with exit status 2
And the compilation does not acknowledge my citations.
Instead it puts a question mark.
Though it looks like my bibliography exists just not citations?

commands followed are before the \end{document}
\bibliographystyle{plain}
\bibliography{paper}

Anybody know how to fix this?

---

### Post by vrangforestillinger on 2008-06-10
Bibtex can be quite a hassle, because you first need to compile the tex. Bibtex will then use the aux-file and the bib-file you specified in the tex to make a bbl-file. THEN when you compile the tex-file again, the latex-compiler will use the bbl file to set up the citations.

Try to run bibtex in the terminal and see what the error message says (i think Kile might be omitting some messages):

```
bibtex paper
``` where paper is the name of the aux-file without extension

---

### Post by buntu_hugenewbie11 on 2008-06-10
Not the problem.
My problem is the bibliography is created but when Latex compiles it does not read the citations correctly.
Which is seemingly impossible as the bibliography exists.

Thus I keep getting errors that the citation is undefined.
Has anybody had these errors before?

---

### Post by vrangforestillinger on 2008-06-10
Did you try to run bibtex in the terminal to see if there is a more describing error message than just "[BibTeX] finished with exit status 2"?

---

### Post by buntu_hugenewbie11 on 2008-06-10
Yes, my problem actually isn't with exit status 2.
That is a style problem.
My issue is that when I compile I get a bibliography but unfortunately the citations in the file have question marks.
In the output I get:
./fieldpaper.tex:533: Citation 'AUTHOr' on page 28 undefined on input line 533.
./fieldpaper.tex:587: Citation 'odean1998' on page 32 undefined on input line 587.
For all my citations.
When I run it in the terminal bibtex compiles correctly but for some reason it can never read citations correctly.
I am truly at a loss for this.
The packages I am using are:
\documentclass[11pt]{UOfieldpaper}
\renewcommand{\baselinestretch}{1.3}
\usepackage{harvard}
\usepackage{amsmath}
\usepackage{amsthm}
\usepackage{amssymb}
\usepackage{graphicx}
\usepackage{keyval}
\usepackage{geometry}
\usepackage{setspace}
\usepackage{mathrsfs}
\usepackage{subfigure}

---

### Post by hugmenot on 2008-06-10
> **buntu_hugenewbie11 said:**
> 
./fieldpaper.tex:533: Citation 'AUTHOr' on page 28 undefined on input line 533.
./fieldpaper.tex:587: Citation 'odean1998' on page 32 undefined on input line 587.


Are these entries in the .bib file? Spelling?

---

### Post by buntu_hugenewbie11 on 2008-06-11
> **hugmenot said:**
> Are these entries in the .bib file? Spelling?

No they are in the tex file.
I figured out the problem though.
The Harvard style only accepts certain bibliographic styles and though it will make a bibliography its citation are messed up if you do not use one of their styles.

---

