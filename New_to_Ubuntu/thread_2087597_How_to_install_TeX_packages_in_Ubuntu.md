---
title: "How to install TeX packages in Ubuntu"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by duttashantanu on 2012-11-24
Hello world!
I am having a problem on installing "Bengali-Omega" package in my Ubuntu 12.04 OS. I have downloaded the .zip file but don't know what to do next.[This]("http://www.tex.ac.uk/tex-archive/help/Catalogue/entries/bengali-omega.html") is the package site.
Will any of you guys please help me installing the package?

---

### Post by alphacrucis2 on 2012-11-24
> **duttashantanu said:**
> Hello world!
I am having a problem on installing "Bengali-Omega" package in my Ubuntu 12.04 OS. I have downloaded the .zip file but don't know what to do next.[This]("http://www.tex.ac.uk/tex-archive/help/Catalogue/entries/bengali-omega.html") is the package site.
Will any of you guys please help me installing the package?

According to the README file in that archive, the install instruction are in a pdf file under the included doc folder.

---

### Post by duttashantanu on 2012-11-24
The installation instructions are only for Windows.
[CENTER][SIZE=3][U][COLOR=Red]!!THERE IS NO INSTRUCTION FOR ANY LINUX VARIANTS!!
[/COLOR][/U][/SIZE][/CENTER]

---

### Post by newb85 on 2012-11-24
If the only instruction included are for Windows, that probably means the package you downloaded can only be run on Windows.

I'm not familiar with bengali-omega, but generally, you should be able to find alternative native Linux apps for TeX document processing.  Maybe you should have a look at LyX.

---

### Post by Impavidus on 2012-11-24
OK, Bengali-Omega is not in the texlive-lang-indic package so you have to install it manually indeed. And in case of fonts that's not easy, especially without a manual. But I've done it before, so I'll try and guide you through.

The best place for manually installing latex packages is in the local texmf tree. Make sure it exists and create some more directories:```

sudo mkdir -p /usr/local/share/texmf/doc/bengali-omega/examples/
sudo mkdir -p /usr/local/share/texmf/fonts/map/dvips/bangla/
sudo mkdir -p /usr/local/share/texmf/fonts/source/bangla/
sudo mkdir -p /usr/local/share/texmf/fonts/type1/bangla/
sudo mkdir -p /usr/local/share/texmf/omega/ocp/
sudo mkdir /usr/local/share/texmf/omega/otp/
sudo mkdir -p /usr/local/share/texmf/tex/latex/bangla/

```Now unpack the zip file and move the files:```

unzip bengali-omega.zip
sudo mv bengali-omega/doc/Manual-Bengali-omega-tex.pdf /usr/local/share/texmf/doc/bengali-omega/
sudo mv bengali-omega/examples/* /usr/local/share/texmf/doc/bengali-omega/examples/
sudo mv bengali-omega/fonts/map/Bangla/bang.map /usr/local/share/texmf/fonts/map/dvips/bangla/
sudo mv bengali-omega/fonts/source/bangla/* /usr/local/share/texmf/fonts/source/bangla/
sudo mv bengali-omega/fonts/type1/bangla/* /usr/local/share/texmf/fonts/type1/bangla/
sudo mv bengali-omega/omega/ocp/* /usr/local/share/texmf/omega/ocp/
sudo mv bengali-omega/tex/latex/* /usr/local/share/texmf/tex/latex/bangla/

```I've never used .ocp files, but they seem to be related to input encoding. In the default texmf tree they are in omega/ocp, so we can best direct them there.

Now you have to tell TeX and friends that you've some new files for them. First make sure all files are readable by all.```

sudo chmod -R o+rX /usr/local/share/texmf/
sudo texhash
sudo update-updmap
sudo updmap-sys

```Now test it. There will probably be some errors. For one thing, I haven't seen any .tfm files yet and they should be there. You should be able to generate them from the .mf files.

PS: Even the font system of LaTeX is completely platform independent, which is why installing fonts is so complicated. I don't think any LaTeX package is windows-only, or whatever-other-OS-only. The documentation says it should run on other systems.

---

### Post by duttashantanu on 2012-11-25
I tested the *'_[COLOR=Blue]ExampleV.tex[/COLOR]_'* file in Examples in *'_[COLOR=Blue]TeXworks'[/COLOR]_*. It gave the following error:-
   [LEFT]```

! Undefined control sequence.
l.5      \ocp
             \bengA=bengvelthuis2unicode
? 
Process interrupted by user

```[/LEFT]
There were 3 columns.It was in the rightmost[3rd] column. In middle column was number 5 and in 1st column was,```
/usr/local/share/texmf/tex/latex/bangla/obeng.sty
``` printed.

---

### Post by Impavidus on 2012-11-30
I'm sorry it took me a few days to answer.

It seems your package installed fine, the problem is probably in the installation of omega, in which I am no specialist. I managed to reproduce your error. Omega is a TeX engine that handles 16-bit character codes and an alternative to the standard pdftex (note the first few lines in your log file, it should tell you which engine you use). According to some posts/blogs/manual pages that google gave me omega does run on Ubuntu and can be called from the command line with "omega example.tex" or (preferably) "lambda example.tex", but after installing the "texlive-omega" package from the ubuntu repository those commands seem unavailable.

Furthermore, omega seems almost dead, so it will be hard to get support.

PS: Omega can be installed manually (I hope). You can download it from [http://www.ctan.org/tex-archive/systems/omega/linux](http://www.ctan.org/tex-archive/systems/omega/linux). Install the binaries in some location in your PATH, put the .fmt files in some sensible location (I suggest where you find the other .fmt files) and hope it works.

---

### Post by frisket on 2012-12-11
> **duttashantanu said:**
> Hello world!
I am having a problem on installing "Bengali-Omega" package in my Ubuntu 12.04 OS. I have downloaded the .zip file but don't know what to do next.[ This]("http://www.tex.ac.uk/tex-archive/help/Catalogue/entries/bengali-omega.html") is the package site.

That page explicitly says it is designed for use with the Omega variant of TeX. If you want to use this package, you must be running Omega, not regular TeX.

Having said that, the zip file appears to contain the normal files for a TeX font installation, so you should install them the same way as for other [La]TeX fonts.

If you are using Ubuntu 12.10 with texlive-full (2012) installed, then the Bangla fonts are already installed for you.

If you are using an older version, the standard method is:

1. unzip bengali-omega.zip into /tmp

2. move everything from the bengali-omega subdirectory into your personal TeX directory (~/texmf) and allow all the directories to merge

3. create ~/texmf/tex/latex/bangla

4. move all the files (autobm.tex thru Ubang.fd) from ~/texmf/tex/latex to ~/texmf/tex/latex/bangla (they should never have been distributed like this: it is an author error)

5. rename Ubang.fd to lowercase ubang.fd because the uppercase letter is a Windows error

6. run updmap --enable Map=bang.map

Unfortunately while this installs the fonts, the package won't work under standard LaTeX; you must be using Omega.

///Peter

---

