---
title: "Simple TeX question"
date: 2007-03-05
forum: Programming Talk
---

### Post by mahy on 2007-03-05
Hi folks,

i need to find a way how to input special chars into TeX using their Unicode position. In Docbook, you can type &number; and it'll compile correctly. How can i do the same in LaTeX? THX.

---

### Post by hod139 on 2007-03-05
Which special characters do you want?  Here are some links to packages you can use:
[LIST]
[*][Unicode text with Pdflatex]("http://ipe.compgeom.org/pdftex_2.html")
[*][Chinese/Japanese/Korean package]("http://cjk.ffii.org/")[/LIST]

---

### Post by mahy on 2007-03-05
I need Hebrew letters. I just downloaded the package cjhebrew (a .zip file), but i really don't know how to install it. Any ideas?

---

### Post by hod139 on 2007-03-05
I'm pretty sure that Hebrew is already supported in LaTeX2e without having to download anything.  See [this page]("http://sites.huji.ac.il/tex/hebtex.html") and check out the bottom two links.

---

### Post by frisket on 2007-03-08
If you're using Emacs, add Norman Walsh's xmlunicode.el 
This provides a M-x iso8879-character-insert function

---

