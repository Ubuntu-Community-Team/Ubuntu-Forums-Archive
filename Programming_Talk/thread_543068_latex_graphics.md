---
title: "latex graphics"
date: 2007-09-04
forum: Programming Talk
---

### Post by nitro_n2o on 2007-09-04
hi all, 
i'm not sure if this is really programming or not, however, i was wondering how to align a photo with text in pdf latex. i.e. I want the photo to appear with the text (say on the right side) and there will be some text on its left. 

any ideas?

---

### Post by nanotube on 2007-09-05
i think this is what you need:
[http://en.wikibooks.org/wiki/LaTeX/Floats%2C_Figures_and_Captions#Wrapping_figures](http://en.wikibooks.org/wiki/LaTeX/Floats%2C_Figures_and_Captions#Wrapping_figures)

---

### Post by gnusci on 2007-09-05
Maybe this code can help you...

```

\documentclass[10pt]{article}

\usepackage{wrapfig}
\usepackage{graphicx}

% Title Page
\title{Hello, World!}
\author{Me}

\begin{document}
\maketitle

\begin{abstract}
This is an introduction to wrapping figures in \LaTeX
\end{abstract}

\section*{Wrapping figures}

\begin{wrapfigure}{r}{40mm}
  \begin{center}
    \includegraphics[width=7cm]{your_picture_here.eps}
  \end{center}
  \caption{my figure}
\end{wrapfigure}

Although not normally the case in academic writing, an author may prefer that some floats do not break the flow of text, but instead allow text to wrap around it. (Obviously, this effect only looks decent when the figure in question is significantly narrower than the text width.) The package wrapfig was developed for this very task.

\hspace*{2mm}

To use wrapfig, you must first add:
\begin{verbatim}
	\usepackage{wrapfig}
\end{verbatim}
to the preamble. This then gives you access to the  command:

\begin{verbatim}
\begin{wrapfigure}{alignment}{width}
  \begin{center}
    \includegraphics[width=7cm]{myfigure.eps}
  \end{center}
  \caption{my figure}
\end{wrapfigure}
\end{verbatim}

Alignment can be either l for left, or r for right. The width is obviously the width of the figure. An example is the figure 1.

\end{document}


```

---

### Post by nitro_n2o on 2007-09-06
Thx guys for your help this is really great :)

---

