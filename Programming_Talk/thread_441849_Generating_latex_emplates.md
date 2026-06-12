---
title: "Generating latex emplates"
date: 2007-05-13
forum: Programming Talk
---

### Post by orlox on 2007-05-13
Hi all!

I'm looking for a way to generate a latex template for corporative documents.As a first aproach I need a way to display a logo at the top and the bottom of the document (as shown in the atached file, that was made using microsoft word...)

I think this is related to working with cls and sty files, yet I haven't been able to find a place that says how to do this simple thing :(

---

### Post by orlox on 2007-05-13
Found a partial solution.

To include a backgroung image in all the document pages I added this to the preamble:
```

\usepackage{eso-pic,graphicx}
\makeatletter
\newcommand\BackgroundPicture[2]{%
  \setlength{\unitlength}{1pt}%
  \put(0,882){%
  \parbox[t][\paperheight]{\paperwidth}{%
    \vfill
    \centering\includegraphics[width=7.5in]{#1}
    \vfill
}}} %
\makeatother
\AddToShipoutPicture{\BackgroundPicture{fondoSinergiaUC}{0}}%

```

here "fondoSinergiaUC" is the name of the backgroud picture. To adjust a different image it's needed to adjust the size at the \include graphics, and the positioning at the \put command. I included a pic in case someone is interested on checking how this looks.

It's really simple and I didn't have to touch any cls or sty files!

---

### Post by xadder on 2007-05-14
Very nice!

You can probably do such things with fancyheadings, fncychap, fancyhdr or similar packages, but it would take some work. I am not sure which is best these days. Would be useful to avoid the need for Word though.

---

### Post by engla on 2007-05-14
I don't know how to, but the cleanest thing would be to make a .sty file for your company, so that all your changes just go into a \usepackage{companystyle} or such

or a style package for that particular document type..
\documentclass[a4paper,mycompany]{article}

---

### Post by rplantz on 2007-05-14
Some techniques for doing this are described in Chapter 18 (Letters) of the excellent book, "Guide to LaTeX, Fourth Edition" by Helmut Kopka and Patrick W. Daly. In particular, see sections 18.2, "A house letter style," and 18.3, "A model letter customization."

I also highly recommend "The LaTeX Companion, Second Edition" by Frank Mittelbach and Michel Goossens.

And I second the poster who advises trying to avoid MS Word. I have written a 500-page textbook that was nearly impossible to maintain in Word. The conversion to LaTeX involved a steep learning curve for me a few years ago. But that effort has been returned many times over in subsequent work on the book. And the finished product is very professional looking. I only wish that I had started with LaTeX.

---

