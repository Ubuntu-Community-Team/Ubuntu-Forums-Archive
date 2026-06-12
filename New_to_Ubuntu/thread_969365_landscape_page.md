---
title: "landscape page"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by zanii on 2008-11-03
Hi all,

I am a new user of Ubuntu 8.04 with Latex, I have one problem in using Latex. I have tried to find a solution of changing portrait page to landscape while inserting an image.

Will anyone please help me with this,only one  landscape page  is supposed to be between portrait pages.

---

### Post by Stefan_K on 2008-11-03
Hi,

to get pages with landscape orientation you could use the [lscape]("http://ctan.org/pkg/lscape") package. If you use pdflatex then use [pdflscape]("http://ctan.org/pkg/pdflscape") instead.
Here's a compilable example for use with pdflatex:
```
\documentclass[a4paper,11pt,demo]{article}
\usepackage[english]{babel}
\usepackage{blindtext}
\usepackage{pdflscape}
\usepackage{graphicx}
\begin{document}
\blindtext[4]
\begin{landscape}
\blindtext
\begin{center}
  \includegraphics[width=.6\textwidth,height=.5\textheight]{test}
\end{center}
\blindtext
\end{landscape}
\blindtext
\end{document}
```
Stefan

---

### Post by zanii on 2008-11-04
Hi Stefan,

I have tried but still nothing happens

---

### Post by Stefan_K on 2008-11-04
Hi Zanii,

> **zanii said:**
> 
I have tried but still nothing happens

what does that mean? Did you get no output? Did you get portrait oriented pages? Or did you get error messages or warnings?
Perhaps post a [minimal working example]("http://minimalbeispiel.de/mini-en.html") that shows the problem.

Stefan

---

