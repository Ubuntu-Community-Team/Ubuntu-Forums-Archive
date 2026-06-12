---
title: "Latex \subsubsection is ignored"
date: 2008-03-06
forum: Programming Talk
---

### Post by DBQ on 2008-03-06
For some reason \subsubsection fails to give heading a section number, although it is treated like a heading.  \section, and \subsection work as they should.  Any idea why?

---

### Post by shifty2 on 2008-03-06
its fine with me:
```
\documentclass[10pt,a4paper]{article}
\usepackage{ifpdf}
\usepackage[utf8]{inputenc}
\usepackage[UKenglish]{babel}
\title{}


\begin{document}
	\maketitle
	\subsubsection{hello}
\end{document}

```
edit:
you may have a * in there? ie \subsubsection*{} that prevents the numbers from appearing

---

### Post by DBQ on 2008-03-06
Your example works - I think it has to do with many strange packages I am using.

---

### Post by frisket on 2008-03-20
> **DBQ said:**
> For some reason \subsubsection fails to give heading a section number, although it is treated like a heading.  \section, and \subsection work as they should.  Any idea why?

Your document class or some package probably sets secnumdepth to 2. 

See [http://latex.silmaril.ie/formattinginformation/chapter3.html#secnum](http://latex.silmaril.ie/formattinginformation/chapter3.html#secnum)

P

---

### Post by nephritiri on 2008-03-20
hmmm.. maybe one of the ways to solve that is to paste your work in a working template.

one i can suggest is use the document class IEEEtrans.cls (of course, download and save it in your working dir first).

\documentclass[journal]{./IEEEtran}

---

### Post by nb_666 on 2008-04-23
> **nephritiri said:**
> hmmm.. maybe one of the ways to solve that is to paste your work in a working template.

one i can suggest is use the document class IEEEtrans.cls (of course, download and save it in your working dir first).

\documentclass[journal]{./IEEEtran}


or just add 
```
\setcounter{secnumdepth}{3}
``` 
to your main document!

---

### Post by nb_666 on 2008-04-24
> **DBQ said:**
> Your example works - I think it has to do with many strange packages I am using.

you may be using **report** on your docmentclass:
```
\documentclass[10pt,a4paper]{report}
```
and not:
```
\documentclass[10pt,a4paper]{article}
```
with **article** it works but with **report** it doesn't if you don't add ```
\setcounter{secnumdepth}{3}
``` 
to your main document

---

### Post by viduliya on 2008-05-06
> **frisket said:**
> Your document class or some package probably sets secnumdepth to 2. 

See [http://latex.silmaril.ie/formattinginformation/chapter3.html#secnum](http://latex.silmaril.ie/formattinginformation/chapter3.html#secnum)

P

Thank you.  This helped alot.

---

### Post by jpfguambe on 2008-12-22
good! it helped me 2!

---

### Post by jeneverboy on 2009-10-19
Hey, it helped me 3!!
Although it does not show in the table of contents??

---

### Post by Zugzwang on 2009-10-19
> **jeneverboy said:**
> Although it does not show in the table of contents??

See here for a solution: [http://www.archivum.info/comp.text.tex/2008-08/00597/Re:_adding_subsubsection_in_table_of_contents](http://www.archivum.info/comp.text.tex/2008-08/00597/Re:_adding_subsubsection_in_table_of_contents)

---

### Post by TammieSeo on 2010-08-07
> **jeneverboy said:**
> Hey, it helped me 3!!
Although it does not show in the table of contents??

I had to run "pdflatex <filename.tex>" in the terminal twice before the table of contents is updated. Try that and see if it works.

---

### Post by frisket on 2010-08-13
> **TammieSeo said:**
> I had to run "pdflatex <filename.tex>" in the terminal twice before the table of contents is updated. Try that and see if it works.

Also check to see if you need to change the value of tocdepth, which controls how far down the tree the ToC goes.

---

