---
title: "New ReadyLaTeX &quot;distribution&quot;"
date: 2009-01-06
forum: Other OS Talk
---

### Post by Nonno Bassotto on 2009-01-06
Hi, I've been creating a "distribution" optimized to write in LaTeX. It's called Ready LaTeX and you can find it [here]("http://www.mat.uniroma1.it/~ferretti/readylatex/"). I callit "distribution" because it is actually not much more than a Kubuntu remix, but enough to have to remove the Ubuntu name and logo and so on... :)

It is meant to be used live either on a CD or on a pendrive,and contains:
    * Most of TeXlive packages, updated to the version in Kubuntu 8.04.1
    * Some other packages not present there, notably kuvio, classicthesis and diagrams among others.
    * The Kile and TeXmaker editors
    * XFig for drawings
    * Asymptote and PGF if you prefer to create your graphics from source.
    * Lots of guides both for general use of TeX/LaTeX and for specific packages.
    * LaTeX support for English (UK and USA), Italian, French, German, Spanish, Portuguese, Russian, Danish, Swedish, Polish and Greek.
    * Some other nice features, just have a look at the website.

If you try it out, let me know here what do you think. In particular, it contains a script to automate install on pendrive, and I'd like to have comments about it working properly or not. It should be safe, but be sure to read the "Readme - Pendrive" inside the Pendrive folder on the Desktop.

A known bug is that it crashes before giving the final dialog which confirms that the install to pendrive is finished. When the file "syslinux.cfg" is on the "readylatex" partition, the install process is actually finished. I still do not understand where the issue resides.

For more detail, just look the webpage above, and please, just let me know if you try it and in case if you find it useful.

---

### Post by jken146 on 2009-01-08
Looks good, but is there any chance of you doing a GNOME or XFCE version?

---

### Post by Nonno Bassotto on 2009-01-09
No, until they feature a decent LaTeX editor :) The most usable on Gnome seems to be Gedit with the LaTeX plugin, but it has many bugs.

---

### Post by smartboyathome on 2009-01-09
Does this include LyX? I love LyX, but it seems to struggle on Arch. Plus, I'm in Calculus and hear it will help with writing proofs. :)

---

### Post by Nonno Bassotto on 2009-01-10
No, it doesn't. I may think about including it in next release, but I'm not sure using Lyx is good practice.

---

### Post by smartboyathome on 2009-01-10
> **Nonno Bassotto said:**
> No, it doesn't. I may think about including it in next release, but I'm not sure using Lyx is good practice.

It is good for those who want to use LaTeX without having to learn all the code. Kind of like why Ubuntu exists. ;)

---

