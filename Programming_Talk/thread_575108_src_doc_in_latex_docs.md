---
title: "src doc in latex docs"
date: 2007-10-13
forum: Programming Talk
---

### Post by nitro_n2o on 2007-10-13
Hi all, 
I want to put some src code in a latex document, does anybody have an idea about that? 
I've downloaded the listings package and compiled it, but I don't know where to put the files (*.sty and *.cnf) in ubuntu. Still, if i leave it in the same dir with the *.tex I get many weired errors for only trying to use it 

here is my code: 
```
\documentclass{article}
\usepackage{listings}

\begin{document}

\lstinputlisting{code.c}

\end{document}
```

Thx

---

### Post by hod139 on 2007-10-14
You can get the listings package by installing either 
tetex-extra 
or 
texlive-latex-recommended

Depending on if you are using tetex or texlive (I suggest you use texlive over tetex)

---

### Post by Vox754 on 2007-10-14
Linux distributions come with command line utilities to manage paths to the files latex and friends use.

```

texconfig

```
Displays the configuration of the system.

You may use
```

kpsepath
kpsepath tex

```
to view the available paths.

In general, you would place new, downloaded packages in the relevant local trees.
```

TEXMFMAIN=/usr/share/texmf
TEXMFDIST=/usr/share/texmf-{texlive,tetex}
TEXMFLOCAL=/usr/local/share/texmf
TEXMFHOME=/home/user/texmf
TEXMF={/home/user/.texmf-config,/home/user/.texmf-var,/home/user/texmf,/etc/texmf,!!/var/lib/texmf,!!/usr/local/share/texmf,!!/usr/share/texmf,!!/usr/share/texmf-{texlive,tetex}}

```
The {} and !! notation is somewhat special but it's explained in the manuals as a way to recursively search directories.
Those variables are not accessible from bash but are internal variables set for the "Kpathsea" search system.

If you want something quick I would suggest placing new packages in your own home folder.

In my case I needed a more recent version of the "subfig" package, and I also downloaded "lipsum", so I created the following structure
```

/home/user/texmf
/home/user/texmf/tex
/home/user/texmf/tex/latex/
/home/user/texmf/tex/latex/lipsum
/home/user/texmf/tex/latex/lipsum/lipsum.sty
/home/user/texmf/tex/latex/subfig
/home/user/texmf/tex/latex/subfig/subfig.sty

```

Whenever you add something new remember to update the database with "texconfig", which actually calls "mktexlsr".

Alternatively you can use the environmental variable TEXINPUTS to add other paths. It's specially useful to locate images.
```

TEXINPUTS=.:./eps:./png:

```
This variable is searched before anything else in the system.
In this example, it will search two directories and then the usual directories.
TEXINPUTS is just like PATH, if you modify it you may want to set it permanently in one of bash resource files, like "/home/user/.bashrc".

As final note, remember that teTex is no longer maintained so it is recommended to use Texlive from now on.
There is no huge difference between the two, just a few new utilities and slightly different structure.

---

