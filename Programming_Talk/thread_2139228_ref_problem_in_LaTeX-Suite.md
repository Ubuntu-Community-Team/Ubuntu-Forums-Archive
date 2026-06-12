---
title: "\ref problem in LaTeX-Suite"
date: 2013-04-26
forum: Programming Talk
---

### Post by mattia.tamellini on 2013-04-26
Hello everyone!

I am experiencing some problems with \ref autocompletion in LaTeX-Suite 1.8 plugin for VIM 7.3 running on Ubuntu 12.04.
Let's say, for example, that I have a multi-file LaTeX project organized like this:
bibliography.bib
doc2.tex
doc3.tex
main.tex
main.tex.latexmain


where main.tex is the main file and doc2.tex, doc3.tex are included via \include{...} command.
The problem is that when I write ```
\ref{
``` and hit F9, the list of possible labels for autocompletion contains only the labels defined in main.tex, while those defined in doc2.tex and doc3.tex are not listed. This happens when trying to autocomplete a reference both in main.tex and doc2.tex and doc3.tex. 
Note that the references works, once I write them by hand (that is, the file compiles and the equations are referenced correctly), I just can't seem to be able to make autocompletion work.

In main.tex.latexmain I wrote:
```
:let g:Tex_ProjectSourceFiles='main.tex doc2.tex doc3.tex'

```
but even if I give the command
```
:let g:Tex_UseSimpleLabelSearch=1
```
the problem remains.

What am I missing?

---

### Post by mattia.tamellini on 2013-04-28
Ok, I got it! Here's the solution, in case anyone gets here looking for it.
It all works out of the box, the only thing to pay attention to is not to leave any blank spaces or tabulations between the beginning of the line and the \include{...} command, otherwise LaTeX-Suite will fail to parse the name of the file included correctly and thus that file will not be browsed for labels once you hit F9

---

