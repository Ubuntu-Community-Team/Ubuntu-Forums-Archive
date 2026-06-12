---
title: "Latex"
date: 2006-12-21
forum: Programming Talk
---

### Post by sameen on 2006-12-21
Salam O Alaikum Brothers!

 i might be out of topic but in UBUNTU i saw tex viewing ubuntu i am asking u a question related to .tex files 

my teacher has done PHD in Maths from an university in England during that time he used a word processor "LATEX" & he wrote many thesis in LATEX now he is back in Pakistan & he wants to publish those thesis but unfortunately he cannot open those files because he dont have latex with him 

so plzz tell me from where i can get latex 
i downloaded a package of miktex. it says that the latex is included in that package but i wasnt so plzz help us out

---

### Post by raul_ on 2006-12-21
```

p   vim-latexsuite                                                          - View, edit and compile LaTeX documents from within vim 

```

U need to have vim installed though

---

### Post by hod139 on 2006-12-21
You don't need to have vim installed.  Install the package tetex.  You probably also want tetex-extra (contains amsmath packages).  If you want an editor, I suggest kile, but gedit works fine too.

---

### Post by sameen on 2006-12-21
i want latex for win xp

---

### Post by christhemonkey on 2006-12-21
Try MiKTeX:
[http://www.miktex.org/Default.aspx](http://www.miktex.org/Default.aspx)

---

### Post by sameen on 2006-12-21
> **christhemonkey said:**
> Try MiKTeX:
[http://www.miktex.org/Default.aspx](http://www.miktex.org/Default.aspx)

i tried that but its useless 

anyother ?? plz z

---

### Post by UbuWu on 2006-12-21
> **sameen said:**
> i want latex for win xp

[Lyx]("http://www.lyx.org/")

---

### Post by bieber on 2006-12-21
Ah, I *love* LyX.  Been using it for school papers and stuff, and it's awesome.

---

### Post by derjames on 2006-12-21
> **bieber said:**
> Ah, I *love* LyX.  Been using it for school papers and stuff, and it's awesome.

Yes use LyX, it will save you a lot of time learning the markup language...  you can use later the LaTeX commands to fine-tune your document...

---

### Post by derjames on 2006-12-21
and it is available for Windows,  Linux, etc...

---

### Post by bieber on 2006-12-21
That it is.  Also, sameen, I have LaTeX installed on my machine, and I'm sure a lot of the people around here do as well, so if you post .tex files we can convert them to PDFs and/or DVIs and/or Postscript files for you.

---

### Post by sameen on 2006-12-22
plzz send me latex ???

---

### Post by sameen on 2006-12-23
> **bieber said:**
> That it is.  Also, sameen, I have LaTeX installed on my machine, and I'm sure a lot of the people around here do as well, so if you post .tex files we can convert them to PDFs and/or DVIs and/or Postscript files for you.

if the latex's setup is too big then share it in torrent plzz

---

### Post by bieber on 2006-12-23
You don't seem to be understanding here.  I run LaTeX on GNU/Linux, and you seem to want it on XP.  If you download LyX for Windows, it includes LaTeX, or you can post the files here and we'll take care of it for you.

---

### Post by sameen on 2006-12-23
> **bieber said:**
> That it is.  Also, sameen, I have LaTeX installed on my machine, and I'm sure a lot of the people around here do as well, so if you post .tex files we can convert them to PDFs and/or DVIs and/or Postscript files for you.



thankx alot friend u helped me lot 
those .tex files rn't mine they are of my teacher


thnkx u for ur cooperation

---

### Post by jan247 on 2006-12-23
```
sudo apt-get install kile kpdf texmaker
```

---

### Post by std on 2006-12-25
I'd rather recommend LyX *with* MikTeX. Although LyX can import LaTeX files, I've found that to be somewhat unreliable at times. LyX won't work by itself and you will need MikTeX (or some other TeX distribution) anyway.

If by "opening a TeX file" you were refering to viewing the contents, TeX files are plain-text so you can open them with anything that does plain-text, even Notepad. MikTeX includes only the tools and files you need to get output from (La)TeX files, like turning the PhD thesis into a PDF, DVI, PS, RTF, HTML file or whatever else you need.

---

### Post by Vox754 on 2006-12-25
Latex files are like *source* code, they are plain text. You can view them with any text editor such as *notepad*, *MSWord*, *WinShell*, *TeXnicCenter*, *kile*, *kate*, *vim*, *gedit*, *emacs*, or many others.

To use the files you need to *compile* them with a TeX Compiler.

*MiKTeX* is a distribution for Windows that contains the compilers, but also viewers, and additional tools to make your life easy. I really doubt that MiKTeX installation would fail.
To install MiKTeX you can download a small file (like 4 MB) that further downloads the rest of the minimum required *packages* (like 30 MB).
Then there is a simple installer that configures everything and you are set in minutes.
Then I would suggest installing TeXnicCenter as an editor and aid for compiling.

You can further download packages up to 300 MB; these are *not* essential but may be useful for a particular task.

If you have the resources, you can download *ProTeX* which is like 750 MB; it contains everything from MiKTeX, plus editors like *WinShell*, *TeXnicCenter*, and *Ghostscript*, and manuals and stuff.
-------------------------------------------------------------------------------------------------
Personally, I learned this way: MiKTeX + TeXnicCenter + lots of documentation.
I haven't tried *etex* in Linux, but I've heard is pretty good.

---

### Post by Verminox on 2006-12-25
Semi-on-topic question: If LaTeX files are created by compiling the .tex files, how come it is used as an interpretted syntax on MediaWiki (eg. Wikipedia). Is it a modiifed version of the LaTeX compiler or is the word "compile" used here entirely different from compiling C/C++.

---

### Post by sameen on 2007-01-02
ohhh my God!!!

i am confused now i have downloaded Protext & installed Miktex + GSV + TeXnicCenter

now i don't know what to do where is latex & all that

my teacher just told me that when u have found latex then run latex & type "/alpha" then run it & it will display alpha sign if i prosper then bring the latex for me 

so plzz brothers help me out of it

---

### Post by amo-ej1 on 2007-01-02
i'm afraid that'll be a little more complex than that. And besides it's \alpha not /alpha and that will only work in math mode...

@Verminox: Those wiki's and forum plugins rely on a LaTeX backend, but for performance sake, the rendered images are buffered and as long as the formulae don't change the buffered copy will be sent to your browser.

---

### Post by Vox754 on 2007-01-02
[QUOTE="Verminox"]Semi-on-topic question: If LaTeX files are created by compiling the .tex files, how come it is used as an interpretted syntax on MediaWiki (eg. Wikipedia). Is it a modiifed version of the LaTeX compiler or is the word "compile" used here entirely different from compiling C/C++.[/QUOTE]
Yeah. I'm using the word "compile" in a very broad way. I just meant that it is a *source* that goes through an *interpreter* and it gives you a result.

[QUOTE="sameen"]my teacher just told me that when u have found latex then run latex & type "/alpha" then run it & it will display alpha sign if i prosper then bring the latex for me[/QUOTE]
I think you are refering to the "command line" in windows, the emulated DOS prompt.
```

C:\Windows>

```
Although it is possible to work from there, most users will work with a text editor with everything integrated in order to understand TeX markup.

You can type this in the command line.
```

C:\Windows> latex file.tex

```
and some output should say that a "file.dvi" was created, or give you some errors.
The "DVI" file is the result and you can view it by double clicking it. The viewer installed with MiKTeX is YAP (Yet Another Previwer).
You can also try
```

C:\Windows> yap file.dvi

```

Later you can convert the DVI file to PDF or, optionally, you can compile the file directly with
```

C:\Windows> pdflatex file.tex

```
giving "file.pdf" as a result.

However, if you installed TeXnicCenter (after MiKTeX), at its first run it will configure itself quickly.
Now you can open any *.tex file with TeXnicCenter. Markup is detected and if you want to process it you have a menu that says "Build".
The shortcuts are to use "Ctrl+F7" for building, and "F5" for previewing the output.

Try this example
```

\documentclass[11pt,draft]{book}
\begin{document}
Insert some text in here.

Mathematics: $\sqrt{\pi}$
\end{document}
```
save it as "01.tex", open it with TeXnicCenter, build it and preview it.
You should also try the command line.

---

### Post by venik212 on 2007-02-01
Either WinEDT (great program, but not free) or TeXnicCenter, which is free.  Sadly, both only work for Windows.

---

### Post by etotehpii on 2007-02-13
> **jan247 said:**
> ```
sudo apt-get install kile kpdf texmaker
```

I just got that and have been trying some code.  How do I view the final product?  I'm a total noob at this, I figured it out on windows with the Miketex and was able to view the final product.  Does kile compile the code so you can read it?

Also it seems to give me errors when I want to view it as a dvi.


[ViewDVI] Could not find the kviewerpart library.


[ViewPS] Could not find the libkghostviewpart library.

I tried sudo apt-install these two files but it couldnt find it.  Do I need to enable something to search for these files?

Thanks

---

### Post by venik212 on 2007-02-14
My guess is that you need to install Latex (tetex or texlive), and then run texconfig (from the terminal).  Try to copile (latex) a latex file from the terminal, to check your latex system.  In addition, Kile has a "check system" option somewhere, probably under TOOLS.  Only after making sure that Latex works on your system, can you hope that Kile will function as a (GUI) front end for latex.
Also, make sure you have a dvi viewer-- kdvi or Adobe Reader.

---

### Post by Steveire on 2007-02-14
> **etotehpii said:**
> I just got that and have been trying some code.  How do I view the final product?  I'm a total noob at this, I figured it out on windows with the Miketex and was able to view the final product.  Does kile compile the code so you can read it?

Also it seems to give me errors when I want to view it as a dvi.


[ViewDVI] Could not find the kviewerpart library.


[ViewPS] Could not find the libkghostviewpart library.

I tried sudo apt-install these two files but it couldnt find it.  Do I need to enable something to search for these files?

Thanks

You are seeing those errors because Kile by default thinks it is running on kde. You are not using kde i guess so you don't have kghostview etc.

Settings > Configure Kile > Tools.

Change the commands for viewDVI viewPs and viewPDF to whatever is used on Gnome. It might even be in the drop down menu.

---

### Post by etotehpii on 2007-02-15
You are correct, I'm using Gnome.

So the general rule of thumb is if an application has a K in front its for KDE?

Anyways these lines of code got things working.

sudo apt-get install kdvi

sudo apt-get install kghostview

Check System told me what I needed to get.:) 

Thanks

---

