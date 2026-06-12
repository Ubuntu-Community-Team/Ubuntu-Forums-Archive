---
title: "Latex - Remove spacing + more question"
date: 2006-05-23
forum: Programming Talk
---

### Post by christooss on 2006-05-23
Hello
I have three little questions but firs one is the most important one

1. How can I remove a spacing on the page

If I use ```
\voffset=-1.5in
``` everything goes UP but I don't want page number go up to.

In attachment you have dvi and tex file so you can see what I mean with 

I would like to have everything on one page



2. How can I remove little spacing that first line in paragraf doesn't have but second line and all other does

```
first line
    second line
    third line

```
look at attachments for this to

3. another question even though I use```
 \pagestyle{empty}
``` there is a page number on the bottom

Thanks for the anwsers

---

### Post by rplantz on 2006-05-24
I'm not a LaTeX guru, but I think that I have figured out at least part of your problems.

First, \maketitle is meant to create a title page. I do not know why you did not get a separate title page, but I suspect that is the reason your page numbering is weird.

I changed your document to use the multicol package. Then I removed the twocol option from the \document command. Then I did
```

\begin{document}
\begin{multicols}{2}[\LARGE{List s forumlami za Ra\v cunalniske tehnologije}]
\normalsize
\section*{Fotoefekt}

```

The columns look a bit odd to me. (I do not know how you want it to look.) You may be able to fix this by modifying the \textheight value. I use the layout package when I want to change these values. Use the command
```

\begin{document}
\layout

```
to print a page showing all the values of the page layout. (Don't forget to do a \usepackage{layout} in the preamble.) Then in the preamble (before the \begin{document}) you can do things like
```

\setlength{\marginparsep}{15pt}
\setlength{\marginparwidth}{117pt}

```
It requires a bit of planning on your part to make sure that all the dimensions add up correctly, buy you now have a lot of control.

I learned this stuff writing a 400 page book about assembly language. I learn new things every time I work on the book. :)

---

### Post by christooss on 2006-05-24
When I use

```
\begin{document}
\begin{multicols}{2}[\LARGE{List s forumlami za Ra\v cunalniske tehnologije}]
\normalsize
\section*{Fotoefekt}

```
I get this out put when preforming

```
latex formule.tex
```

```
! LaTeX Error: Environment multicols undefined.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

l.7 \begin{multicols}
                     {2}[\LARGE{List s forumlami za Ra\v cunalniske tehnolog...

```

So tell me which enviroment I have to set. And how. Or you can send me or post here yours changed forumle.tex file

---

### Post by christooss on 2006-05-24
Hugh that \layout option helped me alot.

Then I only had to put \textheight=700pt in preambule and now there is only one page not two.

But question about multicol package that I have to use still remains :)

And question about paragraf spacing is there to solve :)

---

### Post by christooss on 2006-05-24
[QUOTE=christooss]
And question about paragraf spacing is there to solve :)[/QUOTE]

\parindent=0in solves this.

Hooray

---

### Post by rplantz on 2006-05-24
[QUOTE=christooss]
But question about multicol package that I have to use still remains :)
[/QUOTE]

You need the ```
 \usepackage{multicol} statement in the preamble. For example, [code]
\documentclass[12pt]{article}
\usepackage[slovene]{babel}
\usepackage{multicol}
\pagestyle{empty}
\begin{document}
\begin{multicols}{2}[\LARGE{List s forumlami za Ra\v cunalniske tehnologije}]
\normalsize
\section*{Fotoefekt}

```

If you do not have the package, you should be able to find it on [www.ctan.org](www.ctan.org).

---

### Post by yaaarrrgg on 2006-05-24
For equations, you proabably want to use the align tag. 

For example:

```

\begin{align}
    f(x) & = x^2 \\
    g(x) & = x^x 
\end{align}

```

& will set a point of alignment, and \\ forces new row

---

### Post by christooss on 2006-05-24
Nope equations aligning isn't necesary. But thanks for suggestion.

Is there any book manual that is more than just beginers tutorial?

---

### Post by rplantz on 2006-05-24
[QUOTE=christooss]
Is there any book manual that is more than just beginers tutorial?[/QUOTE]

I found the answers I gave to you above in "Guide to LaTeX, 4th edition" by Kopka and Daly. A more advanced book is "The LaTeX Companion, 2nd edition" by Mittelbach and Goossens. I almost did not buy "Guide" thinking that I knew enough to go straight to "Companion." It turns out that I use both books a LOT.

---

### Post by hod139 on 2006-05-24
[quote=christooss]

Is there any book manual that is more than just beginers tutorial?[/quote]

For a free online manual, check out [The Not So Short Introduction to LATEX2.]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf")
If you plan on writing lots of math, [User’s Guide for the amsmath Package]("ftp://ftp.ams.org/pub/tex/doc/amsmath/amsldoc.pdf") and [Short Math Guide for LATEX]("ftp://ftp.ams.org/pub/tex/doc/amsmath/short-math-guide.pdf") are invaluable.

---

