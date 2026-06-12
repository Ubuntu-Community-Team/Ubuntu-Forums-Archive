---
title: "LaTeX - problem with enumitem package"
date: 2010-04-19
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-19
Hi everyone,

I am trying to use the enumitem package in LaTeX but it is causing a serious problem - if I import it, it seems to break the compilation and it just finishes saying it couldn't find my document.  I am importing it as usual, with \usepackage{enumitem} near the beginning of my document, where I import all the other packages.

If it is of any help I am also using 
```

\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage{amsmath}
\usepackage[pdftex]{graphicx}
\usepackage{url}

```

and they all work fine.

Does anybody have any idea why this might be happening?  It is because of one of the other packages I am using, or do I need to import something else to be able to use enumitem?  I've searched for this online but to no avail.

Thanks in advance!

---

### Post by NovaAesa on 2010-04-19
I replicated your problem, so at least now you know that it's not just you. I don't know what the problem is though, and probably don't have time to help you with it (I'm procrastinating from my pending assignment as I type...).

```
l.1 \usepackage{
                enumitem}
No file test.aux.

! LaTeX Error: The font size command \normalsize is not defined:
               there is probably something wrong with the class file.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

l.3 \begin{document}


! LaTeX Error: The font size command \normalsize is not defined:
	       there is probably something wrong with the class file.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

l.5 \end{document}

[1] (./test.aux) )
(see the transcript file for additional information)
Output written on test.dvi (1 page, 148 bytes).
Transcript written on test.log.
```

---

### Post by Zugzwang on 2010-04-20
So both of you did put the "\usepackage{enumitem}" line *after* the "\documentclass{...}" line? According to [this page]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=normalszmiss"), this is the most common cause of the error you are getting.

---

### Post by mcweaver1 on 2010-04-20
I just tried putting \usepackage{enumitem} before \documentclass{...} and it caused an error saying "LaTeX Error: \usepackage before \documentclass".... Shame, thanks though :)

Lol, good to know it's not just me being retarded and you also had an issue with this!

---

### Post by Zugzwang on 2010-04-20
@OP: Please try to compile the following minimal example:
```

\documentclass{scrartcl}
\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage{amsmath}
\usepackage[pdftex]{graphicx}
\usepackage{url}
\usepackage{enumitem}

\title{Hello World}
\author{Arthur J. Testing}
\begin{document}
\maketitle

\section{A test}
This is a test.

\end{document}

```

Does it compile using pdflatex?

---

### Post by mcweaver1 on 2010-04-20
I am using TeXnic Center and it's not compiling in there... I think the issue is I need to have the package actually downloaded (i.e. enumitem.sty with all the other packages).

I downloaded enumitem.sty and followed some instructions, ([http://www.inf.ed.ac.uk/systems/tex/new-packages.html](http://www.inf.ed.ac.uk/systems/tex/new-packages.html)) which say "alternatively, you could put all of the .sty etc. files into the same directory as the document you are editing" - which I did, and this then let the program compile without any errors and produced the number of pages I was expecting.

However, normally I can view the pdf in Adobe Reader with the shortcut F5 in TeXnic Center; now I just get an error "[DocOpen("%bm.pdf")][FileOpen("%bm.pdf")] Cannot Execute the Command".  I had previously got this error when I first used TeXnic Center because I hadn't set up the "viewer" settings in Build -> Define Output Profiles but then I fixed it and it worked as normal.

I can still open the pdf manually from the directory however, and it looks as I expected.  So I guess the main issue is that you need to have enumitem.sty downloaded to get the enumitem package to work.

Any ideas on my new little problem though?  Guess it's not really a big deal but it is rather annoying....

---

### Post by Zugzwang on 2010-04-20
> **mcweaver1 said:**
> I am using TeXnic Center and it's not compiling in there... I think the issue is I need to have the package actually downloaded (i.e. enumitem.sty with all the other packages).


Well, in that case you probably messed something up. Since you are using TeXnic Center, I assume that you use Windows. As Miktex >= 2.8 should have that package, I would suggest switching to Miktex >= 2.8 and letting its package manager fetch that stuff automatically should do the trick.

---

### Post by mcweaver1 on 2010-04-21
I have now sorted this; when installing MiKTeX I only did a basic installation and this did not include the enumitem package.  For anyone who might need to know I just went to MiKTeX -> Maintenance -> Package Manager and from there found enumitem and then installed it.

Thanks for the help guys!

---

### Post by maparrar on 2012-06-06
> **Zugzwang said:**
> @OP: Please try to compile the following minimal example:
```

\documentclass{scrartcl}
\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage{amsmath}
\usepackage[pdftex]{graphicx}
\usepackage{url}
\usepackage{enumitem}

\title{Hello World}
\author{Arthur J. Testing}
\begin{document}
\maketitle

\section{A test}
This is a test.

\end{document}

```

Does it compile using pdflatex?

Works for me, thanks a lot.

---

