---
title: "LaTeX On Ubuntu 8.04"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by shoaibi on 2008-09-26
I am trying to edit some tex files and recompile them on ubuntu. For that i followed the community docs and installed the texLive, not its full version as i have limited hd space left and then i install TexMaker, my all time favourite tex editor.

Now when i build files i get errors like:
```

! LaTeX Error: File `paralist.sty' not found.

```
 OR in the other file:
```

! LaTeX Error: File `sectsty.sty' not found.

```

aren't these file included in standard distro? do i have to manually download it?

I also tried using different editors such as Kile, WineFish, but same thing... What do you suggest?

---

### Post by Idefix82 on 2008-09-26
You might have to add the relevant bits via Synaptic.
By the way, an extremely efficient and comfortable way of editing Latex files under Gnome is in Gedit with the Latex plugin.

---

### Post by shoaibi on 2008-09-26
idefix82:
i am trying one, can you elaborate a little over this to help me?
and how to do it in gedit? i can edit, but problem is building, getting dvi and pdf files, also texmaker is quite user friendly, i save my typing by two clicks and can add tables, pictures, and etc... but still wanna know about this gedit latex plugin..

---

### Post by Dill on 2008-09-26
I don't know if those files *should* be included on the LaTeX distribution, but you can find them here:

paralist.sty : [http://www.astrosmo.unam.mx/rmaa/OLDLATEX/paralist.sty](http://www.astrosmo.unam.mx/rmaa/OLDLATEX/paralist.sty)
sectsty.sty : [http://www.pingo.org/knjiga/tex-public-0/sectsty.sty](http://www.pingo.org/knjiga/tex-public-0/sectsty.sty)

Make sure you keep them in the same directory as your .tex file when you create the dvi/pdf . 

Cheers, 
Dylan

---

### Post by shoaibi on 2008-09-26
Dill:
okay now i get error on lastpage.sty, do i have to manually download all the sty files required one by one?

---

### Post by Dill on 2008-09-26
Yes. If you include a package at the beginning of your LaTeX document...

```
\usepackage{package name}
```

... you must include the associated sty file in the directory in which you compile the .tex file.

Just google the filename and you should find it quickly enough.

Cheers, 
Dylan

---

### Post by tacutu on 2008-09-26
instal tetexlive-latex-extra. it has all the 3 packages you mentioned. a simple search in synaptic revealed the package.
And no, it doesn't matter what editor you use --- that's just irrelevant to (La)TeX

Dill: no, you do not need to put the sty file in the same directory as the tex file. You can, but it's simpler to create your own texmf tree in your home folded and put the files there.

---

### Post by Idefix82 on 2008-09-26
This is the plugin I was talking about:
[http://live.gnome.org/Gedit/LaTeXPlugin]("http://live.gnome.org/Gedit/LaTeXPlugin")
It's extremely user friendly with clever auto completion, predefined scripts for making pdfs, dvis, very nice intergation of BibTex (like it offers you all the possible citations when you say \cite{ provided that a bib file is defined in the document) and lots more.

---

### Post by Dill on 2008-09-26
Rock on, tacutu. Thanks for the info.

Cheers, 
Dylan

---

### Post by Stefan_K on 2008-10-12
Hi shoaibi,

you could find LaTeX packages by the search feature of Synaptic and would get the package mentioned by tacutu.
If you want to install certain packages instead of the bigger packages by Synaptic or apt-get you will find the latest versions on [CTAN]("http://www.ctan.org/").

I've installed the MiKTeX package manager to install and update packages, that's quick and comfortable. If you are interested, here's an installation description: [The MiKTeX Package Manager 2.7 on Ubuntu Linux 8.04]("http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/").
The next version of this package manager will have a GUI, it's already available as beta version, though later the tlmgr of TeX Live could replace it for me perhaps.

Stefan

---

### Post by b49P23TIvg on 2009-06-29
tex package installation reference:
[http://www.tex.ac.uk/cgi-bin/texfaq2html?label=inst-wlcf](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=inst-wlcf)

Since the  forum answers  are to include  teaching, I'll  condense the
above reference for  you even though I'm sure you  will find it rather
clear.  Substituting for TeX another application, these steps are fairly
generic installation instructions.  The paths and databases differ.

  Download the source:     wget in new directory
  Build the source:             latex the .ins file
  Cleanup:                          rm unnecessary files
  Put it where TeX can find it: sudo mv
  Inform TeX:                     sudo texhash

These  aren't  exactly the  commands  I  used.   When I  followed  the
instructions at the link in my own unique way the expansion

  TEXMF=$(kpsewhich -expand-var "\$TEXMFLOCAL" $)

included a  NUL which caused trouble  so I just copied  what it should
have been.  In my case, /usr/local/share/texmf

I  executed approximately these commands.  In  other words, use
your  smarts, don't copy and paste these lines because I didn't test
them.  Along with the .log file there  may others that you can also
remove.  I don't bother with local documentation because of internet
availability, and I expect this package to be easy to use anyway.


bash
set -a
new_dir=/tmp/$RANDOM
FORMAT=latex
TEXMF=/usr/local/share/texmf
mkdir $new_dir
cd $new_dir
wget http://www.ctan.org/tex-archive/macros/latex/contrib/paralist/paralist.{ins,dtx}
latex *.ins
rm *.log
sudo mkdir --parents $TEXMF/tex/latex/
cd ..
sudo mv $new_dir $TEXMF/tex/$FORMAT/paralist
sudo texhash
exit


For some reason I didn't figure out tex cannot find anything in my environment when I run bash in bash.  Perhaps substitute   pushd $new_dir   for   bash   and   popd  for  exit.   Then reset the three parameters back to however you had them, if you care.  The reasons for the bash command were to 1) choose a shell that recognizes the syntax I've used, and 2) to easily protect your environment.  Also  set -a  is irrelevant since the parameters are used only locally.  Maybe I should have tried a package manager as the other people suggested.

---

