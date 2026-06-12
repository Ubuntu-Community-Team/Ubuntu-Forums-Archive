---
title: "Latex (Texlive) and strange behavior with \tableofcontents"
date: 2008-02-21
forum: Programming Talk
---

### Post by DMurray on 2008-02-21
Hi, everybody.

After switching from teTex to Texlive in 7.10, I noticed that the \tableofcontents is not including the not numbered sections.
Lets say that we have "\section*{Conclusions}" and "\section*{Bibliography}", which I don't want to show numbered in the TOC.
They just don't show at all, unless I manually edit the .toc file.
Anyone else had this problem and/or knows how to fix it?
Thanks a lot.

---

### Post by WW on 2008-02-22
You can force an unnumbered section into the table of contents with the \addcontentsline command:
```
\section*{Conclusions}
\addcontentsline{toc}{section}{Conclusions}
```
See, for example, the last couple paragraphs [here](http://web.image.ufl.edu/help/latex/toc.shtml), or google for "latex tableofcontents" and check out any of the first couple links.

---

### Post by DMurray on 2008-02-22
Thank you very much, WW. The code solved the problem perfectly.
I'm just wondering why it used to work in teTex, but not in Texlive.

---

