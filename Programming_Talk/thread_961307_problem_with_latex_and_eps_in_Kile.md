---
title: "problem with latex and eps in Kile"
date: 2008-10-28
forum: Programming Talk
---

### Post by gaarheidswafel on 2008-10-28
Hi everybody,

latex has 0 errors, 0 warnings and still it doesn't display my eps or jpg in the dvi or the pdf file.
After compiling latex it says nothing or pdflatex is says exit with error status 70.

I have already tried usepackage{graphics, graphicx, psfigure, pstopdf, ifpdf etc}
 

Latex compiles all right, but the viewer doesn't make a file with pictures.

I'm using Kile in Ubuntu-->Hardy Heron-->8.04-->gnome environment

here's my tex code
\documentclass[a4paper,11pt,draft]{article}

\usepackage{amsmath}
\usepackage[UKenglish]{babel}
\usepackage{graphics}
\usepackage[dvips, pdftex]{graphicx}
\usepackage{pspicture}
%\usepackage{ifpdf}
%\ifpdf
%\usepackage[pdftex]{hyperref}
%\else
%\usepackage[dvipdfm]{hyperref}
%\fi 


\author{me}
\title{Test}
\date{2008-10-27}


\begin{document}
\maketitle

 bgkhbngkghkjnhjkhnklghnhkglnghkn

\noindent jfmgflgjgfjlfgjglk


\begin{figure}
 \centering
 \includegraphics{test}
 	\caption{test}
	\label{fig:test}
\end{figure}


\end{document}

---

### Post by Paul Miller on 2008-10-28
First, try running LaTeX multiple times over the document (I don't know why this works, but 3 times is usually enough).

If that doesn't work, I'd suggest changing the line
```

\includegraphics{test}

```
to
```

\includegraphics{test.eps}

```
and running LaTeX at least 3 times over the resulting document.

If *that* doesn't work, try converting your figures to pdf with ps2pdf.

---

### Post by Stefan_K on 2008-10-28
Hi,

just remove the option *draft* in this line:
> **gaarheidswafel said:**
> 
\documentclass[a4paper,11pt,draft]{article}

because the draft option suppresses the inclusion of graphics, just boxes with the filename will be displayed.

Regarding these lines:
> **gaarheidswafel said:**
> 
\usepackage{graphics}
\usepackage[dvips, pdftex]{graphicx}
just
```
\usepackage{graphicx}
```
is enough. graphics will be loaded by graphicx. Don't set driver options like dvips and pdftex if it's not really necessary, it should be automatically detected.
You could find some useful documents concerning the import of graphics with LaTeX [here]("http://texblog.net/latex-link-archive/graphics/").

Stefan

---

### Post by gaarheidswafel on 2008-10-30
Thank you Paul and Stefan!

the solution of Stefan worked!

Thanks very much! \\:D/

---

### Post by frisket on 2008-11-05
> **gaarheidswafel said:**
> Thank you Paul and Stefan!

the solution of Stefan worked!

Thanks very much! \\:D/

It would be very useful to those of us who write LaTeX documentation if you could say where you got the idea for mixing \usepackage{graphics,graphicx} so that we can make it clearer that \usepackage{graphicx} is usually all you need.

---

### Post by Manju116 on 2012-08-07
figures are not getting added in doc after i run latex in kile on ubuntu

\documentstyle{llncs}
\newtheorem{observation}{Observation}
%\usepackage{graphicx}
%\usepackage{epstopdf}
\title{Improved Average Interference in Wireless Sensor Networks}
\author{}
\institute{Department of Computer Science and Engineering,\\ Tezpur University,
Assam, 786028, India
 \and
Department of Mathematics,\\Indian Institute of Technology, Guwahatii, 781 - 039, India}
\date{}
\begin{document}
\maketitle
\input{psfig.sty}

\begin{abstract}

---

### Post by Zugzwang on 2012-08-08
> **Manju116 said:**
> figures are not getting added in doc after i run latex in kile on ubuntu


Note that it is typically advisable to start a new thread here if the older thread is .... very old.

First, why did you comment out "\usepackage{graphicx}"?

Second, try to run "pdflatex <yourpaper>.tex" from the terminal and see if it hangs somewhere. Kile sometimes suppresses certain errors.

Third, "\input{psfig.sty}" is a very weird line - where did you got that from? Typically, you would rather want "\usepackage{psfig}", and this command has to be put *before* "\begin{document}".

Finally, if these things do not work, build a *minimal, complete LaTeX code example* that shows your problem, and post it here together with the LaTeX output you received. There problem with your post here is that id doesn't actually show the lines of the document in which some figure is added.

---

