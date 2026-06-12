---
title: "Latex coding help"
date: 2006-01-12
forum: Programming Talk
---

### Post by neoflight on 2006-01-12
all,

I was looking around for a good forum in latex. but couldnt find any friendly forums as this one with **realtime** response. zillions of help is available in documentation but hard to find any 'specific' solution. 

i am just trying to have one in this forum too since i/we spend a lot of time here...

any ideas? or is it redundant?
the objectives i have in mind are:

1. how to set up latex (any kind) installation in ubuntu or other.
2. how to set up a frontend and compile
3. how to write the scripts for various disciplines
4. ohw to install packages and such
5. how latex is being treated in ubuntu
6. future version of latex
7. anyother you think is appropriate

iam myself a noobeee in ubuntu and latex. but getting most of my oxygen from this forum...please let me know. 

thank you all.

---

### Post by paulmilliken on 2006-01-12
[QUOTE=neoflight]
1. how to set up latex (any kind) installation in ubuntu or other.
2. how to set up a frontend and compile
3. how to write the scripts for various disciplines
4. ohw to install packages and such
5. how latex is being treated in ubuntu
6. future version of latex
7. anyother you think is appropriate
.[/QUOTE]
 
You will find latex in the repositories so you can use Synaptic to install it as well as the dependencies.  It's also useful to install dvips or dvipdfm which will allow you to convert your compiled documents (.dvi files) to ps or pdf files for easy printing or sharing.

As far as learning LaTeX goes, there are numerous online tutorials including [http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/](http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/)

Paul

---

### Post by Viro on 2006-01-13
I think it isn't the amount of tutorials that is the problem, rather the availability of forums where if you're stuck, you can go to for help. I think it's a great idea :).

---

### Post by neoflight on 2006-01-14
[QUOTE=Viro]I think it isn't the amount of tutorials that is the problem, rather the availability of forums where if you're stuck, you can go to for help. I think it's a great idea :).[/QUOTE]


thats what i thot too...its good for beginners who get stuck quite often and there will always be beginners...!!! like me..

---

### Post by Delkster on 2006-01-14
I don't know exactly what you mean but I just thought I'd express my view that having a single thread for a broad subject such as latex generally isn't a very good idea. If you have a question that is unrelated to the existing discussions (whether latex or not), post a new thread.

That way things get organized within the forums in such a way that old discussions regarding certain topics should be relatively easy to find and browse later, and that's a significant part of the value of such discussions. If there's just a single gigantic thread for everything latex, finding out whether it already contains the solution for your specific problem can be a pain because you may well need to scan through the entire thread for that.

Edit: Of course it's quite likely that a thread regarding latex wouldn't grow to gigantic proportions very quickly in a place like this so it just *might* be a good idea after all.


Whether discussion concerning latex should be in the programming forum, I wouldn't comment on that. Neither the description of the forum nor the guidelines for posting specify whether subjects such as markup languages and other non-programming languages should be conversed here.

---

### Post by Viro on 2006-01-14
I don't think we're talking about posting all LaTeX related questions in just this thread. Rather, it's about creating a specific forum for it.

---

### Post by karih on 2006-01-14
Latex can be installed with the following command:
$ sudo apt-get install tetex-base tetex-bin
Then you can for example try the following code in file eg test.tex:
```
\documentclass[a4paper,11pt]{article}
\begin{document}
My first \LaTeX{} document.
\end{document}
```
Then run in terminal
$ latex test.tex
$ xdvi test.dvi   -- will open the dvi file
$ dvips test.dvi -- will convert the dvi file to ps file

Hope this helps

---

### Post by jpkotta on 2006-01-14
I learned LaTeX last fall.  In a few hours I knew almost everything I needed to generate a good document using [The Not So Short Guide to LaTeX]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf").  It's the best reference I've found so far.  Whenever I get stuck, e.g. an error that doesn't make sense, I just copy the error and Google it, and usually the fix is right there.  

I use Emacs for writing LaTeX.  Try installing AUCTeX from the repos; it has tons of easy to learn macros for writing LaTeX documents.  You'll probably want amsfonts and tetex-extra too.  For compiling, I just run pdflatex to generate straight to pdf:```
pdflatex document.tex && acroread document.pdf
```With pdflatex, you can also get hypertext and color.

One thing that I remember struggling with was BibTeX, which the guide doesn't have too much on.  Google a bit and you'll find help.  If you like, I'll make a short guide to BibTeX.

Another thing that may mess you up is underscores.  Always use '\_' in text mode, or the verbatim environment.  You'll get a cryptic error that goes something like "not in math mode" (because underscore is only allowed in math mode).

---

### Post by jerome bettis on 2006-01-16
here's a nice makefile my prof wrote for us, just change the first line to the first part of your tex file and you should get a pdf among whatever else. latex is really nice, i havent used word (or :shudder: open office) for a long time.

```
FILE_NAME = report

TEX_FILES = \
$(FILE_NAME).tex

DVI_FILES = \
$(FILE_NAME).dvi

PS_FILES = \
$(FILE_NAME).ps

PDF_FILES = \
$(FILE_NAME).pdf

BIB_FILES = \
$(FILE_NAME).bib

all: $(PDF_FILES) tidy_up

test:
        echo $(PDF_FILES)

pdf: $(PDF_FILES) tidy_up

ps: $(PS_FILES) tidy_up

dvi: $(DVI_FILES)

$(FILE_NAME).dvi: $(TEX_FILES) $(BIB_FILES)
        rm -f $(FILE_NAME).dvi *.aux
        sh -c 'latex $(FILE_NAME).tex' 
        sh -c 'latex $(FILE_NAME).tex'   # do this twice cause latex is funny
        bibtex $(FILE_NAME)
        sh -c 'latex $(FILE_NAME).tex'
        sh -c 'latex $(FILE_NAME).tex'   # again & again for good measure

%.ps: %.dvi
        rm -f $@
        dvips -t letter $< -o $@

%.pdf: %.ps
        rm -f $@
        ps2pdf $< $@

tidy_up:
        rm -f *.dvi *.aux *.bbl *.blg *.log *.toc

clean: tidy_up
        rm -f $(DVI_FILES) $(PS_FILES) $(PDF_FILES)
```

---

### Post by jerome bettis on 2006-01-16
[quote=jpkotta]Another thing that may mess you up is underscores. Always use '\_' in text mode, or the verbatim environment. You'll get a cryptic error that goes something like "not in math mode" (because underscore is only allowed in math mode).[/quote]

use vim with the latex-suite package, it makes bad things show up in red right away so you know to put the \ there.

---

### Post by kakk on 2006-01-31
I'd like to have a separate forum for latex. Here or somewhere else. If you know of something of the kind available, please write the address here.

---

### Post by toojays on 2006-01-31
You could try the usenet group comp.text.tex.

---

### Post by dada1958 on 2006-02-16
I highly recommend "LaTeX A Document Preparation System" by Leslie Lamport and "The LaTeX Companion" by Goossens, Mittelbach and Samarin. Both are published by Addison Wesley and obviously made with LaTeX :cool:

---

### Post by halfvolle melk on 2006-02-16
Kile ([http://kile.sourceforge.net/](http://kile.sourceforge.net/)) is nice as well. Works great, also on Ubuntu.

I'd recommend the following documentation (depending on your needs):
[http://www.tug.org/tex-archive/macros/latex/contrib/fancyhdr/fancyhdr.pdf](http://www.tug.org/tex-archive/macros/latex/contrib/fancyhdr/fancyhdr.pdf)
[http://www.ctan.org/tex-archive/macros/latex/contrib/booktabs/booktabs.pdf](http://www.ctan.org/tex-archive/macros/latex/contrib/booktabs/booktabs.pdf)
[http://www.ctan.org/tex-archive/macros/latex/contrib/psfrag/pfgguide.pdf](http://www.ctan.org/tex-archive/macros/latex/contrib/psfrag/pfgguide.pdf)

The best way of learning it may be to get the source of a finished document and study it (after reading the Not So Short Introduction).

---

### Post by dada1958 on 2006-02-16
[ This one](http://www.tex.ac.uk/tex-archive/info/beginlatex/html/intro.html#intro) can also be useful. And there is an excellent PDF, beginlatex, which can be found [here](http://www.ctan.org/tex-archive/info/beginlatex/).

I use [TeXMaker 1.3](http://www.xm1math.net/texmaker/) as front end editor, installation is a breeze and it doesn't require the KDE libraries if you're working with Gnome. It's written by the guy who was the man behind Kile until version 1.5.

---

### Post by neoflight on 2006-02-17
I finally managed to make texlive and texmaker work together. 
[Here is a how]("http://www.ubuntuforums.org/showthread.php?t=131507&highlight=texlive")-to on that. Please let me know ur comments and such. 

Any additions are welcome.

Thanks

---

### Post by hod139 on 2006-02-18
I don't think a separate thread is needed for latex specific help, there isn't one for C or Java or Python etc.

I think simply posting questions in the programming thread when you have one is best. 

There already is a ubuntu wiki page about setting up latex. [https://wiki.ubuntu.com/LaTeX](https://wiki.ubuntu.com/LaTeX)

---

