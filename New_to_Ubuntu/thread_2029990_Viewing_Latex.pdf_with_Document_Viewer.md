---
title: "Viewing Latex.pdf with Document Viewer"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by godfreezone on 2012-07-20
I just made a test .tex file using texmaker.

I know i have a .tex file but can't get Document Viewer to read it.

Error message is: 
Unable to open document
File type Tex document (text/x-tex) is not supported.

Anyone? any suggestions?
thx
God-free

---

### Post by bryncoles on 2012-07-20
have you run LaTeX on the document yet?

Lets say the document is on a folder called 'tex_document' on your desktop.  

Open a terminal and cd to the folder 'tex_document'.  

```
cd ~/Desktop/text_document
```

now, run the command 

```
pdflatex filename.tex
```

to create the pdf file which evince can read.

***edit***

Sorry -- just realised you said texmaker.  There should be an icon on the taskbar which runs the pdf command.  What I said above will work, but it doesn't use texmaker!

---

### Post by bryncoles on 2012-07-20
[http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX)
[http://tobi.oetiker.ch/lshort/lshort.pdf](http://tobi.oetiker.ch/lshort/lshort.pdf)

Here's two useful links for using learning / LaTeX without texmaker (I started with texmaker a few years ago... migrated away though...)

---

