---
title: "install latex document class"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by paper_bridge on 2008-10-03
I am publishing a book with Cambridge University Press. They have written their own LaTeX document class and ask authors to use it. It is called "CUPBOOK.cls".

I am extremely novice with Linux. I have only ever used Add/Remove and Synaptic to add and remove programs. So I do not know how to install this document class to my repository.

Anyone willing to step me through it?

Thanks.

---

### Post by tacutu on 2008-10-03
open up a terminal (Application -> Accesories) and type:
```
mkdir -p ~/texmf/tex/latex
```
assuming that CUPBOOK.cls is in your home directory, type:
```
mv ~/CUPBOOK.cls ~/texmf/tex/latex/
```
finally, do a 
```
texhash
```
That's it, you should be all set now.

---

### Post by Stefan_K on 2008-10-13
Hi,

probably texhash/mktexlsr doesn't search ~/texmf, but it depends on the configuration of course.
On some systems $TEXMFHOME (~/texmf) is searched by kpathsea even without ls-R database there, texhash is not needed then if files are installed in the home texmf directory.
If you install into local, main or distribution directories, you should call
```
sudo texhash
```

Stefan

---

### Post by frisket on 2008-10-14
> **paper_bridge said:**
> I am publishing a book with Cambridge University Press. They have written their own LaTeX document class and ask authors to use it. It is called "CUPBOOK.cls".

I am extremely novice with Linux. I have only ever used Add/Remove and Synaptic to add and remove programs. So I do not know how to install this document class to my repository.

Anyone willing to step me through it?

Thanks.

See chapter 5 of "Formatting Information" about installing packages. [http://latex.silmaril.ie/formattinginformation/chapter5.html#pkginst](http://latex.silmaril.ie/formattinginformation/chapter5.html#pkginst)

---

