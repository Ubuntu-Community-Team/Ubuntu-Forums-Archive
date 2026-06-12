---
title: "[SOLVED] Section Numbering Problem in LaTeX"
date: 2008-07-16
forum: Programming Talk
---

### Post by billynomates on 2008-07-16
Hi, I have a problem. My LaTeX code below works fine, except that the numbering is wrong on the table of contents and section headers. Instead of [FONT="Courier New"]1, 2, 2.1, 3[/FONT], it goes [FONT="Courier New"]0.1, 0.2, 0.2.1, 0.3[/FONT].
Any ideas why?


```
\documentclass[11pt]{report}

\usepackage{url}

\setlength{\topmargin}{-.5in}
\setlength{\textheight}{9in}
\setlength{\oddsidemargin}{.125in}
\setlength{\textwidth}{6.25in}

\begin{document}
\title{Undergraduate Project 1}
\author{Michael Speed\\
Traffic Wales}
\renewcommand{\today}{July 25th 2008}

\begin{titlepage}
\maketitle
\end{titlepage}

\begin{abstract} Abstract abstract abstract.
\end{abstract}

\pagestyle{plain} % No headers, just page numbers
\pagenumbering{alph} % Roman numerals
\tableofcontents
\cleardoublepage

\pagenumbering{arabic}

\section{Overview}
This is a section

\subsection
This is a subsection

\end{document}

```

---

### Post by Zugzwang on 2008-07-16
That's normal behaviour since in the book and report classes, sections are only the second-highest "structural elements" of the text. You need to start with "\chapter{foo}".

---

### Post by billynomates on 2008-07-16
Thanks for you reply.
Hmm, if I change one of them to \chapter{Section Name} instead of \section{Section Name}, it just changes the text to 
> Chapter 1
Section Name
but the Table of Contents stays the same.

:confused:

---

### Post by Zugzwang on 2008-07-16
> **billynomates said:**
> 
but the Table of Contents stays the same.


Did you run Latex two or three times to update the TOC?

---

### Post by billynomates on 2008-07-16
2 or 3 thousand. I'm using MiKTeX on Windows, if that makes a difference (I'm at work). I don't see why it should though.

---

### Post by Zugzwang on 2008-07-16
Don't have a clue why that happens. I modified your example:

```

\documentclass[11pt]{report}

\usepackage{url}

\setlength{\topmargin}{-.5in}
\setlength{\textheight}{9in}
\setlength{\oddsidemargin}{.125in}
\setlength{\textwidth}{6.25in}

\begin{document}
\title{Undergraduate Project 1}
\author{Michael Speed\\
Traffic Wales}
\renewcommand{\today}{July 25th 2008}

\begin{titlepage}
\maketitle
\end{titlepage}

\begin{abstract} Abstract abstract abstract.
\end{abstract}

\pagestyle{plain} % No headers, just page numbers
\pagenumbering{alph} % Roman numerals
\tableofcontents
\cleardoublepage

\pagenumbering{arabic}

\chapter{Overview}
This is a chapter

\section{Stuff}
This is a section

\end{document}

```

...and it works fine. You might try deleting the .toc and .aux files of your document and copy this example.

---

### Post by hod139 on 2008-07-16
Zugzwang already mentioned this, but I'll say it again, you can't use \section as the **top** level in a report; report expects \chapter to be the top level.

---

### Post by billynomates on 2008-07-16
Ok, cool. Deleting the aux and toc files worked, but I don't really want chapters in my report. That's a bit counter-intuitive, don't you think? Surely chapters should be saved for books?

I'd change it to an article but I like the layout for abstracts and title pages that you get in reports. Changing it to an article also messes up my page numbering. :(

---

