---
title: "Why LaTeX is such a bloated system?"
date: 2007-03-28
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2007-03-28
Hi,

I begin to learn LaTeX but I have a question about it. I downloaded the famous "Not so short..." PDF e-book. But to apply the examples, I have to have a LaTeX installation on my system so I looked internet for a lightweight LaTeX software but interestingly after an hour or so I end up with no such a software on my system (I'm looking for Win XP). I saw there is a MikTeX named software and it is the tiniest software about LaTeX on WinXP. Other softwares I found was based on MikTeX. But MikTeX is not lightweight, actually it is huge, even it's "basic setup".

I understand that TeX is a some kind of language to write books etc. and when we "compile" the "source code" (.tex) our output is a .dvi file. My question is that: **Why LaTeX software is such a "huge", "complex" "system"**?

You may ask that "Why are you making this problem?". Because I always use lightweight programmes and LaTeX may be powerful but I feel like it is bloated :( Just a LaTeX software has thousands of files, hundreds of folders, hundreds of .exe files... During installation it installs 2-3 exclusive softwares like Ghostscript etc. and this is the basic setup. There is also a complete setup option. I cannot understand this. It is one of the biggest software I installed on my computer. I have written by now just "Hello World" examples but I am afraid if it will give hundreds of dependency errors when my document gets complexed :)

---

### Post by josephus on 2007-03-28
I recommend using WinEdt if you are doing any reasonable amount of work with Latex.  Provides a nice editor and links everything together quite nicely.  

In all I think latex takes up about 100+/- Mb on my windows system.  I don't know if that is actually a lot or not, but I find it doesn't take up any significant systems resources when I'm working on my document.    Ghostscript is needed to produce postscript files, and with ghostscript viewer is useful for reading postscript files off the net.

---

### Post by dvase on 2007-03-29
I'm no Tex expert, but it seems to me that there are two main reasons for Tex's bloated size:
[LIST=1]
[*]It's a powerful, multifaceted typesetting system, and
[*]There's a lot of backward, legacy compatibility built into the system.
[/LIST]

TeX is relatively old software (since 1978!) and thus it seems to carry a lot of baggage.  However,  the fact that it has survived this long is a testament to its power and versatility.

---

### Post by Zdravko on 2007-03-29
I think LaTeX is bloated too. The MikTeX installation is HUGE! It takes at least 150-200 MB. And do you know what was the nastiest thing at the end? LaTeX has very bad support for cyrillic languages like Bulgarian. This means, that you can use it only in English (or German). Very great, really :(

---

### Post by hod139 on 2007-03-29
> **Zdravko said:**
> And do you know what was the nastiest thing at the end? LaTeX has very bad support for cyrillic languages like Bulgarian. This means, that you can use it only in English (or German). Very great, really :(
LaTeX has had Cyrillic language support since 1998!  Bulgarian is supported in the T2A encoding.  See the [Cyrillic language support in LaTeX guide]("http://tug.ctan.org/tex-archive/macros/latex/doc/cyrguide.pdf") for more help.  The extensive language and font support is one reason LaTeX is so large.

---

### Post by milton1 on 2007-03-29
Yes, LaTeX is a bit big, and on windows it can feel a bit clumsy at times, but it is well worth it. The beauty of the output and ease of formatting technical documents are a dream come true for anyone writing scientific or technical papers, books, etc. I used LaTeX to write my master's thesis, a document containing many extremely ugly equations, and I remain convinced that using this system saved me months of work. LaTeX could be ten times as bloated as it is now, and I would still say it is worth learning and worth using.

---

### Post by Zdravko on 2007-03-29
> **hod139 said:**
> LaTeX has had Cyrillic language support since 1998!  Bulgarian is supported in the T2A encoding.  See the [Cyrillic language support in LaTeX guide]("http://tug.ctan.org/tex-archive/macros/latex/doc/cyrguide.pdf") for more help.  The extensive language and font support is one reason LaTeX is so large.
Have you ever tried to create a document with mixed language - both english/german and bulgarian? Do you know what happens? :(

---

### Post by hod139 on 2007-03-29
> **Zdravko said:**
> Have you ever tried to create a document with mixed language - both english/german and bulgarian? Do you know what happens? :(

You have to use the babel package, which is distributed with texlive and miktex.  There is a huge and very detailed [user guide]("http://tug.ctan.org/tex-archive/macros/latex/required/babel/babel.pdf") (463 page pdf) available.  Bulgarian language supports starts on page 293, English page 20.

---

### Post by rplantz on 2007-03-29
> **milton1 said:**
> Yes, LaTeX is a bit big, and on windows it can feel a bit clumsy at times, but it is well worth it. The beauty of the output and ease of formatting technical documents are a dream come true for anyone writing scientific or technical papers, books, etc. I used LaTeX to write my master's thesis, a document containing many extremely ugly equations, and I remain convinced that using this system saved me months of work. LaTeX could be ten times as bloated as it is now, and I would still say it is worth learning and worth using.

I agree 100%. I started writing a textbook a few years ago using Word on my Macintosh. It was a nightmare. One of the big problems with Word is it does not allow chapters. You can use sections, but these are used for other things. Like changing the number of columns. Then, headers go with the section. So when you change the section to change the number of columns, blah, blah, blah.

I needed to make some big changes in my book. After fighting with Word's problems, I finally took the time to learn LaTeX. I'm still learning, and still amazed at what I can do with it. It has **greatly** simplified writing of my book.

The book, by the way, is over 450 pages and has many program (mostly assembly language) listings. It now looks very professional, something I do not think I could have achieved with Word. (Assuming I could have gotten the headers to behave properly.)

I now do most of my writing -- business letters, slide presentations, etc. -- with LaTeX. Much better looking output and much easier to compose.

As for the bloat, disk space is pretty cheap these days. (I realize that "cheap" is relative, so this may not be the case for everyone.)

---

### Post by ZuLuuuuuu on 2007-03-29
Thank you all for the comments. Although I still think it is a little bloaty, I will give it a try and finish the e-book and some other tutorials. Maybe like milton1 or rplantz I will be very satisfied about the capabilities of LaTeX :)

---

### Post by Paulus on 2007-03-29
once you learn.. latex is amazing!

Nothing beats it for mathematical proofs (apart from written paper).

I wrote my dissertation entirely in latex- 50 pages with diagrams and lots of equations and it looked stunning; soo much better than the word versions my classmates used.

took absolutely ages to learn the code and find the .sty files for wrapping text around images, but it was worth it.

keep at it.

p.s is latex a lost cause on linux?  I couldn't find anything matching winedit for latex support.

---

### Post by rplantz on 2007-03-29
I just use gedit. It has syntax coloring and spell checking. The only hassle is that I have to turn on Tools -> Autocheck Spelling every time I start gedit. I wish there were a way to make this the default. (I find it easier to see my spelling errors with autocheck.)

I then wrote a Makefile:
```

# Makefile for my book

default:
	latex book.tex
	makeindex book.idx
	latex book.tex
	dvips book.dvi

clean:
	rm *.aux
	rm *~

```
So I open a terminal window, and when I want to view my work, I simply type "make" and wait 1/2 minute.

As you can see, my Makefile creates a postscript file, which I view with evince.

I make changes in the source (in gedit), save, hit the up arrow key in the terminal window to recall my "make" command, and hit return. 1/2 minute later I hit ctrl-r in the evince window.

I don't know how this compares to using winedit since I've never used it.

---

### Post by josephus on 2007-03-30
I still prefer winedt, but on linux i find that Kile is a decent substitute.

---

### Post by ZuLuuuuuu on 2007-03-30
rplantz, I also like using plain text editors to write code. Which libraries should I install via Synaptic to be able to use the latex command? Just to be able to compile my .tex files via terminal is enough for me no need to have an IDE.

---

### Post by rplantz on 2007-03-30
> **ZuLuuuuuu said:**
> Which libraries should I install via Synaptic to be able to use the latex command? Just to be able to compile my .tex files via terminal is enough for me no need to have an IDE.

I am using tetex-base, which depends on tex-common. It also suggests tetex-extra and recommends tetex-doc. (To see this information, highlight tetex-base in synaptic and click on Properties.) I have some other things installed, but I don't think you need them.

Having said this, you may wish to think about installing texlive. The tetex maintainer has announced that he will no longer do it and recommends that people move to texlive. Ubuntu lists tetex as the supported system, not texlive. I suspect they were waiting for texlive 2006, which never made it. Texlive 2007 has just been released, but the version in the Ubuntu repositories is texlive 2005.

If I were starting from scratch, I would install texlive. I hope the transition from tetex to texlive will be smooth for me. But I have more faith that the transition from texlive 2005 to texlive 2007 will be smooth.

---

### Post by Zdravko on 2007-04-29
> **hod139 said:**
> You have to use the babel package, which is distributed with texlive and miktex.  There is a huge and very detailed [user guide]("http://tug.ctan.org/tex-archive/macros/latex/required/babel/babel.pdf") (463 page pdf) available.  Bulgarian language supports starts on page 293, English page 20.

Can you give me an example how a simple "Hello world" will look like in LaTeX?
The following:
```

\documentclass[a4paper,12pt]{book}

\usepackage[utf8]{inputenc}
\usepackage[english]{babel}
\usepackage[T1]{fontenc}
\usepackage[dvips]{graphicx}

\author{Monov, Z.}
\title{Introduction to design patterns}
\date{2007-04-29}

\begin{document}

\end{document}


```

Kile issues the errors:
> [LaTeX] intro.tex => intro.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/latex/base/fontenc.sty:100:Font T1/cmr/m/n/12=ecrm1200 at 12.0pt not loadable: Metric (TFM) file not found. \fontencoding\encodingdefault\selectfont
[LaTeX] 1 error, 0 warnings, 0 badboxes

---

### Post by qix on 2007-04-29
You probably also wanna add "\maketitle" between your \begin{document} and \end{document}.

---

### Post by hod139 on 2007-04-29
> **Zdravko said:**
> Can you give me an example how a simple "Hello world" will look like in LaTeX?
The following:
```

\documentclass[a4paper,12pt]{book}

\usepackage[utf8]{inputenc}
\usepackage[english]{babel}
\usepackage[T1]{fontenc}
\usepackage[dvips]{graphicx}

\author{Monov, Z.}
\title{Introduction to design patterns}
\date{2007-04-29}

\begin{document}

\end{document}


```Kile issues the errors:

This code works fine for me.

> 
                             [LaTeX] intro.tex => intro.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/latex/base/fontenc.sty:100:Font T1/cmr/m/n/12=ecrm1200 at 12.0pt not loadable: Metric (TFM) file not found. \fontencoding\encodingdefault\selectfont
[LaTeX] 1 error, 0 warnings, 0 badboxes

This is your problem, you are missing some fonts.  It also looks like you are using tetex, not texlive.  Using the texlive metapackage, everything just works.  With tetex, try installing the package tetex-extra, which will hopefully contain the missing fonts.

---

### Post by Zdravko on 2007-04-30
Yup! This helped!

---

