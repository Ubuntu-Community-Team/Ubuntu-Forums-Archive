---
title: "PNGs in LaTeX"
date: 2007-03-26
forum: Programming Talk
---

### Post by tonyr1988 on 2007-03-26
EDIT: Wrong Forum. I'm sorry. Could someone please move this to Math & Science?

I'm doing a Physics lab report, so I'm reading up on LaTeX for it. I've never used it before, but I've always been interested, and I've got an opportunity to take my time to learn it, so why not? :)

I'm stuck on getting PNGs in there, however. From what I've read, I should be able to do this (I left out all the irrelevant stuff):

> \usepackage{graphicx}

\includegraphics{position_horizontal.png}

However, that gives me this error:

> ! LaTeX Error: Cannot determine size of graphic in position_horizontal.png (no 
BoundingBox).

If I specify width / length, it gives me the same error.

Whenever I change it to this:

> \usepackage[pdftex]{graphicx}

\includegraphics{position_horizontal.png}

It works fine, but the picture is *extremely* small (unreadable). Changing the width, height, and scale don't work.

Any ideas?

Also, I had originally tried to make them *.eps files in Gimp, but the quality of them is absolutely terrible, so I gave up on that.

---

### Post by &lt;mawe&gt; on 2007-03-26
How do you compile your file? With *latex* or *pdflatex*.

---

### Post by tonyr1988 on 2007-03-26
Just *latex*

EDIT: *pdflatex* seems to work perfectly using what the tutorials told me to use. Thanks a ton!

---

