---
title: "HOWTO: TeXLive and Texmaker"
date: 2006-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by neoflight on 2006-02-16
Hi,
[COLOR="Red"]EDIT: Dec 28, 2006:
***If you are using Edgy, then you dont need to follow the Texlive installation instruction. It can be installed after enabling universe repositories. Use of latest version of Texmaker is optional.  Note: Texmaker is also in the repos and should work out of the box with texlive installation via repos.

If you want to remove the old texlive installation (if you have followed this howto) just remove the texlive folder from the /usr/local/ and undo changes made in the .bashrc file. ***[/COLOR]

This HOWTO explains step by step procedure to install **LaTeX - TeXlive**
and a very good front-end for editing called **Texmaker**.

Note: [COLOR="Red"]If you like Kile instead of Texmaker, follow this-[/COLOR][HOWTO]("http://ubuntuforums.org/showthread.php?p=807144") 

Furthermore, this explains also howto install any new [LaTeX package]("http://ctan.org/tex-archive/"), that may be required for your work, into TeXlive installation. 

> Virtually all TL packages come from [CTAN]("www.ctan.org"). |[here]("http://tug.org/texlive/pkgcontrib.html")|

This is as a result of several ideas collected and consolidated from various sources [google, this forum, etc]. 

I am writing this because of 3 main reasons:
1. to use it as a reference for myself in the future as i have a habit of forgetting what i did earlier.
2. there was so much of a confusion to get the texmaker working with texlive and also the texlive itself.
3. to get all the required info at the *same place* [as much as possible].

Various steps are:

**I. Download Texlive.**

1. Obtain TeXlive [here]("http://www.tug.org/texlive/"). The latest version is 2005.
2. [Burn it as iso image into a CD]("https://wiki.ubuntu.com/BurningIsoHowto"). 

**II. Install Texlive2005 to disk.** [this is not for running it live]

1. this is quite easy. mount the texlive2005 CD and navigate to that directory using a terminal.

```
cd /media/cdrom0
```

2. now install process.

```
sudo sh install-tl.sh
```

3. You will be prompted with various options. I didnt change any of the suggested dir locations etc. just do this:
```
 i
``` and enter.

lots of stuff will happen and enjoy the scrolling text...you can smile at the screen if you like :)

4. Now this is very important. set the PATH. [this information is provided in *[The TeX Live Guide]("http://www.tug.org/texlive/doc/texlive-en/live.pdf")* pp.11]

I did this before I could run texconfig. Its good if we could set the PATH first, I think.

```
PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH
```

you can do this at the terminal or put it at the end in /etc/bash.bashrc
This way, the path will be set when you login as this file is run at login. 

```
sudo gedit /etc/bash.bashrc
```

copy-paste the above PATH at the end of the file. save and close.

check the path and make sure that the path is there...
```
echo $PATH
```

discussions on setting env variables can be found [here]("http://www.ubuntuforums.org/showthread.php?t=2793&highlight=%2Fetc%2Fprofile+PATH").

5. Now run 

```
texconfig
```

if it returns 'command not found' the the Path is not set properly. i would suggest re-login after setting the path. Else, what you could do is to run the above path command at the terminal to activate it for the time being.

6. run 
```
sudo texhash
``` 
or
```
sudo texconfig rehash
```
this updates various file name databases. [pp. 13 of tex live guide]

7. make sure it works...at the terminal type,

```
tex --version
```

you should see this:

```
TeX 3.141592 (Web2C 7.5.5)
kpathsea version 3.5.5
Copyright 2005 D.E. Knuth.
Kpathsea is copyright 2005 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.
Kpathsea written by Karl Berry, Olaf Weber, and others.

```

Good. Its working ! Make sure all the tex commands are working by trying at the terminal (any directory) one by one...

latex, dvips, bibtex, gv, makeindex, xdvi, pdflatex, dvipdfm, ps2pdf, xpdf or acroread (install separately and make it executable), and mpost.

if xpdf is not working then you can install it like,
```
sudo apt-get install xpdf
```..

in Dapper you can get acroread7. add this to /etc/apt/source.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

if you need gv then open a terminal

```
sudo apt-get install gv
```

note: if you like to deal with graphics then its good to have gv installed so that you can view you .eps file (it also helps to get the BoundingBox coordinates for advanced graphics handling)

An excellent document on graphics using latex is available in pdf format.
[Using Imported Graphics in LaTeX2e by Keith Reckdahl]("http://www.ctan.org/tex-archive/info/epslatex.pdf")

Note: After you login, the texlive2005 is ready for action. you can navigate to the directory where your .tex files are and use the command line directly to run using appropriate commands, or use gedit or some editor as applicable. But I like Texmaker for its simplicity, user friendly GUI, and light weight set up etc...

I have seen some permission issues preventing the commands running even from the terminal. so you can actually set the permissions using chmod command. Below is a sample (be careful when setting permission: do some research on issues when setting permissions or get help from some guru if in doubt). Couple of good references on this are  [here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html") (detailed) and [here]("http://www.cae.wisc.edu/site/public/?title=linpermissions-change") (brief)

```
sudo chmod -R  755 /usr/local/texlive/2005/bin/i386-linux
```

**III. Download and install texmaker:**

1. download the texmakerunix_install.sh  [here]("http://www.xm1math.net/texmaker/download.html")

2. I moved the file to 

```
sudo mv /usr/local
``` and installed by 

3. ```
sudo sh texmakerunix_install.sh
``` (This is provided in texmaker website ... Qt4 is not required.)
Now texmaker is ready for some customization.

4. Configure texmaker.

Open Texmaker and go to  

```
Options > Configure Texmaker
```

Here is the screenshot of what I have. You dont need to put the entire paths of all commands in there. Just the command will do: for e.g., 
xdvi %.dvi or pdflatex --interaction=nonstopmode %.tex etc., as given in texmaker [documentation]("http://www.xm1math.net/texmaker/doc.html"). 

The idea is, if you have all the latex commands working from the terminal after login then just by giving the commands (without entire path) should work.

5. Using the quick build option.

This is a nice option to use. I use the pdflatex + xpdf to directly convert and view pdf from somefile.tex. if you enter 'acroread' instead of 'xpdf' as in step III-4 would get you the pdf file opened in acroread... [as such...for other applications...] 

NOTE: Texmaker can be used with tetex2/3 as required. Important thing is to have the PATH set up properly. Thats it.
-------------------------------------------------------------------------

**How to add LaTex packages (*.sty/*.bib) etc into Texlive.**

While you are at it, I thought it is a good idea to explain how we could install new LaTeX packages into texlive: [this is a copy of what I have written in one of the messages in the same thread]

In texlive it can be done pretty easily. There are 3 steps involved:

1. Locate my_package.sty file. sometimes it comes as my_package.ins or my_package.dtx. Download it to somewhere easily accessible. 
for e.g., /home/latexpacks

then go to that folder and run

```
cd /home/latexpacks
latex my_package.dtx
```

to get the my_package.sty , etc.

2. Now, create a new folder called my-package here

```
sudo mkdir usr/local/texlive/2005/texmf-dist/tex/latex/my_package
```

then copy the my_package.sty to this dir. 

```
sudo mv my_package.sty usr/local/texlive/2005/texmf-dist/tex/latex/my_package

```
so you have you new package in place now.

2.1 Its good to have a copy of the .ins and .dtx file here like this.


```
sudo mv mypackage.ins /usr/local/texlive/2005/texmf-dist/source/latex/my_package

```

2.2 similarly for my_package.bib (if any)
```
sudo mv my_package.bib /usr/local/texlive/2005/texmf-dist/bibtex/bib/my_package

```
3. Then run,

```
sudo texhash
```

you are set!...It's good to check the documentation of the package to see if you need anyother files...

[HOWTO]("http://ubuntuforums.org/showthread.php?p=807144") [COLOR="Blue"]on using Kile with TeXLive.[/COLOR] 

Thanks in advance for any suggestions/comments/corrections...

Good day and latex away.

---

### Post by dada1958 on 2006-02-17
[QUOTE=neoflight]Hi,
This is where I had several problems mainly due to carelessness.
start texmaker from 'run application' wizard (alt+F2). I dont have texmaker listed in any menus yet (any ideas how to bring that up?)[/QUOTE]

You can make a new menu entry with Applications Menu Editor

You can also assign a keybinding with configuration-editor.

---

### Post by neoflight on 2006-02-17
[QUOTE=dada1958]You can make a new menu entry with Applications Menu Editor

You can also assign a keybinding with configuration-editor.[/QUOTE]

Thanks !!!

---

### Post by dada1958 on 2006-02-17
Now it's time to get [pdftex 1.30.6](http://www.mail-archive.com/ctan-ann@dante.de/msg00574.html) installed :)
The version in TeXLive 2005 is 1.30.4-2.2

---

### Post by kleeman on 2006-02-17
Could you outline the advantages of Texlive over the standard tetex suite of packages that comes with Ubuntu? I'm curious....

---

### Post by neoflight on 2006-02-17
Hi Kleeman,
As far as I know, tetex is derived from texlive distributed by TUG. Supposedly texlive is more up-to-date and has most of the applications that can be distributed in a single installation (and so more complete?), IMK. Tetex negates the platform issue as I am told, if any. 

The standard package tetex2 that comes with breezy is very very out of date...Moreover, I have had problems using packages with tetex2 (tried tetex3 as well backporting from dapper source) as I was getting error messages that those were not loaded. But its not a major issue as one can always get the packages from CTAN.  I felt, texlive, to be easy to configure and install new packages into. I think it depends on what one is used to. 

Other thing I noticed is that, I have the Texlive CD and I can always reinstall it (or add extra packages...if needed) without having to connect to the internet.
Since I am a student there are many journal specific packages available in Texlive. (I dont know about tetex...so not comparing here).

Texmaker and texlive make a good team and I am enjoying it. 
Honestly, I dont have any clue as of any other difference between these two.
Hopefully someone can throw some light on this.

---

### Post by neoflight on 2006-02-17
texlive and tetex- difference?

some googling gave me 
[this]("http://lists.debian.org/debian-devel/2005/06/msg01103.html")

and

[this...]("http://w3.msi.vxu.se/~pku/MacOSX_TeX/2002a/msg00395.html")

It seems to me that texlive is the most comprehensive we can get in a single stroke.

---

### Post by kleeman on 2006-02-17
Thanks neoflight. Sounds like there are two issues 1) comprehensiveness and 2) uptodateness. I guess in dapper with tetex 3 the second is less important. The first bugs me a bit with tetex sometimes.

---

### Post by dada1958 on 2006-02-18
[QUOTE=dada1958]Now it's time to get [pdftex 1.30.6](http://www.mail-archive.com/ctan-ann@dante.de/msg00574.html) installed :)
The version in TeXLive 2005 is 1.30.4-2.2[/QUOTE]

Ok ok ok :-)

Yesterday I downloaded the pdftex-1.30.6.tar.gz and struggled with it without much success. This afternoon I managed it to do the update.

I'll try to describe how :)

Unpack the tar.gz.

Than:
```

$ cd pdftex-1.30.6

$ ./build.sh

```
I got quite a bunch of errors, the output in the terminal was indicating that I missed several packages like gcc, g++, bison and more. Read the output carefully and copy and paste the missing packages in the 'search' window of Synaptic and install them.

When you're done, **delete** the pdftex-1.30.6 directory and unpack the tar.gz again. And there we go again:
```

$ cd pdftex-1.30.6

$ ./build.sh

```
If things went right, you can enter:
```

$ ls build/texk/web2c/{pdftex,pdfetex,pdftex.pool,pdfetex.pool}

```
When you see a green line of text at the bottom of your terminal output you have the files to perform the update. They are in build/texk/web2c/ of the pdftex-1.30.6 directory you unpacked before.

Start Nautilus as root and locate the 'pdfetex' file in /usr/local/texlive2005/bin
and 'pdfetex.pool' in /usr/local/texlive2005/texmf/web2c

Replace those 2 files.

Finally recreate your formats:
```

$ fmtutil --all

```

---

### Post by neoflight on 2006-02-18
thanks dada1958...
i will try it at home...

is this new verison better than the old existing one?

---

### Post by dada1958 on 2006-02-19
[QUOTE=neoflight]is this new verison better than the old existing one?[/QUOTE]

To be honest I didn't encounter shocking improvements but it's always nice to know how to install those packages.

---

### Post by Wes24 on 2006-02-19
Does anybody know how to add documentclasses to tetex of texlive? For my papers I need apa-style and apacite, but I don't know how to add them. I currently use Lyx-Tetex, but it says that APA is unavailable. Help is appreciated:). 

btw, thanks for the how-to, I'm going to try it right away:).

---

### Post by dada1958 on 2006-02-19
[QUOTE=Wes24]Does anybody know how to add documentclasses to tetex of texlive? For my papers I need apa-style and apacite, but I don't know how to add them. I currently use Lyx-Tetex, but it says that APA is unavailable. Help is appreciated:). 

btw, thanks for the how-to, I'm going to try it right away:).[/QUOTE]

AFAIK LyX has its own file format. The [apacite package](http://www.ctan.org/tex-archive/help/Catalogue/entries/apacite.html) is included with TeXLive, I don't know if it's included with teTeX.

---

### Post by neoflight on 2006-02-19
[QUOTE=Wes24]Does anybody know how to add documentclasses to tetex of texlive? For my papers I need apa-style and apacite, but I don't know how to add them. I currently use Lyx-Tetex, but it says that APA is unavailable. Help is appreciated:). 

btw, thanks for the how-to, I'm going to try it right away:).[/QUOTE]

you are welcome!

In texlive you can do it pretty easily. {try it and let me know :D }...

there are 3 steps involved:
1. get the **my_package.sty** file. sometimes it comes as my_package.ins or my_package.dtx. then you have to run 

```
latex my_package.dtx
```

you may have to run it a couple of times. to get the my_package.sty

2. now, create a new folder called my-package here 
```

[CODE]sudo mkdir usr/local/texlive/2005/texmf-dist/tex/latex/my_package
```

then copy the my_package.sty to this dir. so you have you new package in place now. 

Note 1: its good to have a copy of the .ins and .dtx file here
/usr/local/texlive/2005/texmf-dist/source/latex/my_package

Note 2: my_package.bib (if any) can be put here
/usr/local/texlive/2005/texmf-dist/bibtex/bib/my_package

3. run  ```
> texhash
```

you are set!...good to check the documentation of the package to see if you need anyother files...

just post your experiences/corrections please...

---

### Post by kleeman on 2006-02-19
[QUOTE=Wes24]Does anybody know how to add documentclasses to tetex of texlive? For my papers I need apa-style and apacite, but I don't know how to add them. I currently use Lyx-Tetex, but it says that APA is unavailable. Help is appreciated:). 

btw, thanks for the how-to, I'm going to try it right away:).[/QUOTE]

Well according to this list of experimental texlive Debian packages:

[http://lists.alioth.debian.org/pipermail/pkg-texlive-maint/2006-January/000346.html](http://lists.alioth.debian.org/pipermail/pkg-texlive-maint/2006-January/000346.html)

the styles you need are in texlive. 

On my system lyx tries to find apa style but cannot presumably because it is not in tetex. If you installed texlive then I suspect if you reconfigured lyx it would find apa and apacite and you would be ready to go.

It would be really great if the texlive packages made it into Ubuntu from Debian experimental. I wonder also whether the texlive packages from Debian experimental might install on Ubuntu anyway? Maybe not given how extensive tetex is.

---

### Post by neoflight on 2006-02-19
[QUOTE=kleeman]It would be really great if the texlive packages made it into Ubuntu from Debian experimental. 
I wonder also whether the texlive packages from Debian experimental might install on Ubuntu anyway? Maybe not given how extensive tetex is.[/QUOTE]

I doubt it though. People are yelling for tetex3 now. it should be in dapper.

I think, installing deb-exp should not be a problem in ubuntu. never tried.
did you try installing texlive2005? it's really stable and extensive.

---

### Post by kleeman on 2006-02-19
Here's another interesting webpage on Debian and Texlive:

[http://www.tug.org/texlive/debian.html](http://www.tug.org/texlive/debian.html)

---

### Post by kleeman on 2006-02-19
[QUOTE=neoflight]
did you try installing texlive2005? it's really stable and extensive.[/QUOTE]
It sounds tempting actually but I haven't as yet. My issue is always about future system upgrades....

---

### Post by dada1958 on 2006-02-19
I googled a little bit on APA:

> The American Psychological Association has established a style that it uses in all of the books and journals that it publishes. Many others working in the social and behavioral sciences have adopted this style as their standard as well.

The apacite package seems to meet this style and resides in the TeXLive 2005 distribution.

TeTeX 3 will be in the Dapper repositories but I hadn't the patience to wait that long so I switched to TeXLive that is based on teTeX :)
The Debian TeXLive repositories are still in very experimental stage and therefore not operational.

---

### Post by neoflight on 2006-02-19
[QUOTE=kleeman]Here's another interesting webpage on Debian and Texlive:

[http://www.tug.org/texlive/debian.html](http://www.tug.org/texlive/debian.html)[/QUOTE]

thats promising. thanks for the link!

---

### Post by kleeman on 2006-02-19
What would be really neat would be if their was some sort of synaptic style gui interface to ctan such that you could install new style files in latex with a simple "point and click". I have suggested that to the lyx developers.....

---

### Post by neoflight on 2006-02-19
[QUOTE=kleeman]What would be really neat would be if their was some sort of synaptic style gui interface to ctan such that you could install new style files in latex with a simple "point and click". I have suggested that to the lyx developers.....[/QUOTE]

any response from them? it would nice to have some application for all the tex editors. 

i think it would be too much work for so direct a thing. generally, i heard, people are confortable with manually installing the packages...

lets wait and see...

---

### Post by Wes24 on 2006-02-27
Well, it worked perfectly, I now have the APA packages in mij TexLive:). However, the command "texhash" only worked by doing "sudo texhash".

Tnx anyways for this nice How-To:)

---

### Post by neoflight on 2006-02-27
[QUOTE=Wes24]Well, it worked perfectly, I now have the APA packages in mij TexLive:). However, the command "texhash" only worked by doing "sudo texhash".

Tnx anyways for this nice How-To:)[/QUOTE]

Thnaks for the comments wes24. I added a note about sudo above. 
Please feel free to discuss any ideas.

---

### Post by nanotube on 2006-02-28
in reply to your comment about looking carefully in the output and installing various compilers - instead of doing that, you should just install the package called "build-essential", and that will install just about anythnig you need to build stuff. saves you the trouble of looking for a bunch of different compilers. :)

actually, i don't know why ubuntu doesn't come with build-essential by default. ive seen so many people have trouble installing stuff from source, and asking on the forums "why can't i compile". heh.

---

### Post by sherlock-holmes on 2006-03-03
nice..working....!!!

i wish it had a spell checker !!!!
and permission to change the fonts used in the editor by selection...

---

### Post by dada1958 on 2006-03-03
Integrating a spellchecker like aspell could make TeXMaker a killer app, I'm wondering if this is very hard to do in the source code.

You can set the font used in the editor: Options -> Change Interface Font

---

### Post by sherlock-holmes on 2006-03-03
really....a spell checker and some minor tweaks will make it ultimate...

i tried changing the interface font as u mentioned. but it changes only the fonts of icon labels and stuff...not the editor fonts...it is really apparent when i copy paste from OOo or from emails etc.... that particular sections remains whatever fonts they are even though i try to change it many ways...even a texmaker restart...

donno...any clue? thanks...

---

### Post by dada1958 on 2006-03-03
Sorry, my mistake.

Options -> Configure Texmaker, hit the Editor button and you're there.

---

### Post by preyer on 2006-03-08
Don't know if this is the correct place to put this request but I couldn't find the answer anywhere. Please point me in the right direction if I am wrong.

Is there any way to setup Kile so that it is able to use a TexLive installation as shown in the start of this threads? I have installed TexLive correctly but cannot compile when compiling directly with Kile.

Any help will be appreciated, Thank you.

---

### Post by neoflight on 2006-03-09
[QUOTE=preyer]Don't know if this is the correct place to put this request but I couldn't find the answer anywhere. Please point me in the right direction if I am wrong.

Is there any way to setup Kile so that it is able to use a TexLive installation as shown in the start of this threads? I have installed TexLive correctly but cannot compile when compiling directly with Kile.

Any help will be appreciated, Thank you.[/QUOTE]

Hi, I just placed a howto in this. will be up soon... the idea is to have all the path set-up correctly to run the commands...its too long to type again.....[-(

---

### Post by neoflight on 2006-03-11
[QUOTE=preyer]Don't know if this is the correct place to put this request but I couldn't find the answer anywhere. Please point me in the right direction if I am wrong.

Is there any way to setup Kile so that it is able to use a TexLive installation as shown in the start of this threads? I have installed TexLive correctly but cannot compile when compiling directly with Kile.

Any help will be appreciated, Thank you.[/QUOTE]

here is the link to howto use kile with texlive...

[http://ubuntuforums.org/showthread.php?t=141934](http://ubuntuforums.org/showthread.php?t=141934)

pls let me know...

---

### Post by preyer on 2006-03-12
You are awesome, thank you very, very much.

It works perfectly as you said in the how to. Even for pdflatex.

---

### Post by neoflight on 2006-03-12
[QUOTE=preyer]You are awesome, thank you very, very much.

It works perfectly as you said in the how to. Even for pdflatex.[/QUOTE]

thanks for the comments. I am glad that its uesful...

---

### Post by ruddyss4 on 2006-03-25
Hey neoflight, Ive been following the steps accurately and everything is 100% functional. But I am stuck on the last step, where it says how to add Latex packages into TexLive. I have no idea where the my_package.sty/.ins/.dtx file is. Am I missing something?

By the way, thanks for the great "How To", all steps were wonderful. I really needed a "TeX" editor, and you've really helped.

---

### Post by neoflight on 2006-03-25
[QUOTE=ruddyss4]Hey neoflight, Ive been following the steps accurately and everything is 100% functional. But I am stuck on the last step, where it says how to add Latex packages into TexLive. I have no idea where the my_package.sty/.ins/.dtx file is. Am I missing something?

By the way, thanks for the great "How To", all steps were wonderful. I really needed a "TeX" editor, and you've really helped.[/QUOTE]


Thanks for the comments ruddyss4. Actually the packages we mostly need are already there in TeXlive2005. If you want to add 'additional' or 'new' packages that are not in TeXlive installation then follow the steps.... 

this is the case when you are writing a paper/article where it has certain specific format and the template contains a custom package. Just put the packages (e.g.g sty files) in the location specified.... please let me know if you like to have more info on this...

---

### Post by ruddyss4 on 2006-03-25
[QUOTE=neoflight]Thanks for the comments ruddyss4. Actually the packages we mostly need are already there in TeXlive2005. If you want to add 'additional' or 'new' packages that are not in TeXlive installation then follow the steps.... 

this is the case when you are writing a paper/article where it has certain specific format and the template contains a custom package. Just put the packages (e.g.g sty files) in the location specified.... please let me know if you like to have more info on this...[/QUOTE]

Understood.:)  Well besides that, everything else is fine. Now I just have to learn all the syntax; Im new to latex. Any tutorials out there? Thanks neoflight!

---

### Post by neoflight on 2006-03-25
[QUOTE=ruddyss4]Understood.:)  Well besides that, everything else is fine. Now I just have to learn all the syntax; Im new to latex. Any tutorials out there? Thanks neoflight![/QUOTE]


Several....  pretty much everything u can get from google.
But good to have a steady learning track which will help one search better...

1) here is the first one almost everyone uses.....search for lshort.pdf in google and u will get it...

2) link an excellent document for graphics handling is provided in this howto. 

3) here is another online/downloadable one....
[http://www.tug.org.in/tutorials.html](http://www.tug.org.in/tutorials.html)

4) [http://www.geocities.com/kijoo2000/](http://www.geocities.com/kijoo2000/)


etc etc....all you have to do is type latex in google....:D 

hope this helps.... i suggest using kile sometime as a front end...its amazing...and has spell check and 'suggest as you type' .... which saves a lot of time....texmaker is much lighter..... my signature has some tips on using kile with texlive...

hope this helps...

---

### Post by dada1958 on 2006-04-29
Thursday I gave Dapper Drake a shot; it looked really nice, but I couldn't use TeXLive with it yet. Access denied, so I'm back to Breezy.
Are there others having this issue?

---

### Post by neoflight on 2006-04-30
[QUOTE=dada1958]Thursday I gave Dapper Drake a shot; it looked really nice, but I couldn't use TeXLive with it yet. Access denied, so I'm back to Breezy.
Are there others having this issue?[/QUOTE]

no i dont have any problems with texlive....did u try as root?

---

### Post by rplantz on 2006-04-30
[QUOTE=neoflight]texlive and tetex- difference?

some googling gave me 
[this]("http://lists.debian.org/debian-devel/2005/06/msg01103.html")

and

[this...]("http://w3.msi.vxu.se/~pku/MacOSX_TeX/2002a/msg00395.html")

It seems to me that texlive is the most comprehensive we can get in a single stroke.[/QUOTE]
 I just ran across some newer remarks
[here]("http://www.tug.org/pipermail/tex-live/2006-January/009627.html")

I found it quite easy to install TeXLive following the HowTo above. I am updating a 400 page book on assembly language, and my new TeXLive installation did it out of the box.

---

### Post by dada1958 on 2006-05-02
[QUOTE=neoflight]no i dont have any problems with texlive....did u try as root?[/QUOTE]

Problem is solved, I had to chmod the pdfetex updater...

---

### Post by hajk on 2006-05-29
This whole TeX Live thing will become important shortly, as Thomas Esser is reported to announce soon that he will no longer maintain teTeX. If truth be told, even the latest teTeX in Dapper is already a bit long in the tooth when compared with the packages in TeX Live and on CTAN.

It is time, I think, for the Debian TeX Live packages (now in experimental) to be added to the Dapper universe or multiverse repositories.

---

### Post by sherlock-holmes on 2006-06-01
[QUOTE=hajk]This whole TeX Live thing will become important shortly, as Thomas Esser is reported to announce soon that he will no longer maintain teTeX. If truth be told, even the latest teTeX in Dapper is already a bit long in the tooth when compared with the packages in TeX Live and on CTAN.

It is time, I think, for the Debian TeX Live packages (now in experimental) to be added to the Dapper universe or multiverse repositories.[/QUOTE]


Texlive works great for me...i use it with texmaker, gedit, kile whichever seem conveniant for me...
it has all the essential packages for almost all my works + i could easily add any packages/class files that come with a template for my papers...

good...

---

### Post by snl on 2006-07-14
Thank you for a great howto.

I successfully installed both TeXLive and Texmaker. However, if I want to uninstall Texmaker to use Kile, for example, instead, how can I do that?

Thank you.

---

### Post by neoflight on 2006-07-16
> **snl said:**
> Thank you for a great howto.

I successfully installed both TeXLive and Texmaker. However, if I want to uninstall Texmaker to use Kile, for example, instead, how can I do that?

Thank you.

if you go the first original post in  this thread you will find a link to the kile+texlive. else more easily...

[here it is....]("http://www.ubuntuforums.org/showthread.php?t=141934")

---

### Post by krugman on 2006-08-03
Hi to all!

I am new to linux, and used to work with Winedt and Miktex, but as I am trying to switch to ubuntu, I would really like the make that work, but I can't compile with Texmaker, even after I followed the guide. The thing is, I have tetex installed also, is it a problem? I tried texlive because with tetex he was asking for the package epigraph.sty that I downloaded and installed, but still, he didn't seem to find it...
Anyhow...I guess I have some problems with the Path...I guess I did not really understand that part of the tutorial...
Because I get the same error message I used to get with tetex, so, it must mean that texmaker is still looking for tetex and not texlive...

Any help please? I am getting frustrated :(

---

### Post by barmaley on 2006-08-09
Hello, people
Thank you for the How-to.
I have a small problem with the texmaker configuration and I don't manage to solve it. It is the "Log file not found!" problem.
If someone knows how to solve it, please help.
Thank you.

---

### Post by deepspring on 2006-08-09
Thanks for this guide, everything worked flawlessly. 

I've been wanting to try Latex for sometime, just didn't know where to start.

---

### Post by lodbergs on 2006-09-13
> **barmaley said:**
> Hello, people
Thank you for the How-to.
I have a small problem with the texmaker configuration and I don't manage to solve it. It is the "Log file not found!" problem.
If someone knows how to solve it, please help.
Thank you.

Hi

I have the exact same problem. Can someone help?

/Søren

---

### Post by Aramis on 2006-10-18
This is yet another excellent HOWTO. However, I would like to underline a couple issues.

First of all, the shear size of the TeXLive distribution. I am well aware that memory is cheap but it is not always plentyfull. I installed this distribution on my laptop with just 5GB for the root partition after installation I only had a couple of hundreds Megs left! and I had to go to quite a length of trouble to mitigate [ [link]("http://ubuntuforums.org/showthread.php?t=279650") ] .

Second of all, the technique describe to add packages to the LaTeX repository does not seem to work. I have a document that requires the use of the DROPPING package. I checked before following the intruction if the package was on my machine... after all TeXlive takes nearly 3GB, and I could see that the STY file was in the LaTeX folder. I tried to compile the file again... no luck. I followed the instructions, and still no luck. I would really appreciate some help here. I have done the texhash, and rehash. The file is where it should be... but for some reason it seems that TeXMaker (or indeed the command it uses to compile) cannot find it.

Help is more than welcome!

Happy TeXing

Ar@mi$

---

### Post by neoflight on 2006-11-15
> **lodbergs said:**
> Hi

I have the exact same problem. Can someone help?

/Søren

"log file not found" error is one of the most common i have encoutered with latex installations. the problem lies in getting the ide to look at the texlive installation directories. 

So in texmaker if you provide the entire path of the executables for eg: in the case of latex command ....provide...

```
/usr/local/texlive/2005/bin/i386-linux/latex
```

otherwise texmaker wont find the log file created when running latex for the succeeding commands. 

make sure that you can run latex from the command line first. 

more easy way is to get texlive installed from the repositories. its active for edgy. its in the universe.

```
sudo aptitude install texlive-base texlive-latex-base 
```

elase search using synaptics and select which ever texlive packages you need such as texlive-publishers. 

this way you can select only the language support you actually need. the original texlive from tugs has all those built-in which makes it really huge... :) so technically you dont have to follow this howto if you are using edgy. :evil:

---

### Post by nullchina on 2006-11-26
the best guide to texlive2005 I had ever seen,thanks!

---

### Post by barmaley on 2006-11-30
Hello, people
I'm trying to create a document with english and russian words and I get en error
"! Font T2A/cmr/m/n/10=larm1000 at 10.0pt not loadable: Metric (TFM) file not found."
It seems there are some fonts missing. Does anybody know how to add those fonts or necessary package?
Thanks.

---

### Post by kleeman on 2006-11-30
Sounds like you are missing a Russian font of some kind. I have found this page to be a help:

[http://tug.org/TeXnik/mainFAQ.cgi?file=docs](http://tug.org/TeXnik/mainFAQ.cgi?file=docs)

See the fonts sections.

---

### Post by bodhi.zazen on 2006-12-03
Nice How-to

This thread has been added to the UDSF wiki.

[TeXLive_and_Texmaker](http://doc.gwos.org/index.php/TeXLive_and_Texmaker)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by neoflight on 2006-12-04
> **bodhi.zazen said:**
> Nice How-to

This thread has been added to the UDSF wiki.

[TeXLive_and_Texmaker](http://doc.gwos.org/index.php/TeXLive_and_Texmaker)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

Thank you and I really appreciate it...

The texlive distribution is now in th repos for edgy and so the installation is a direct one . So people do not need to download and install things separately. For, installing custom made packages into texlive, the howto may be of some help.

Thanks again.

---

### Post by barmaley on 2006-12-04
Hello, people
I'm again with the same problem. Despite the link above, I do not manage to create a document with russian words. Here is the error that I get in Texmaker:

"! LaTeX Error: Command \cyrn unavailable in encoding OT1."

Does anybody know how to fix the problem?

May be someone knows how to uninstall texlive?
Thank you in advance.

---

### Post by kleeman on 2006-12-04
Do you have the edgy packages installed? If so is this package installed?:

texlive-lang-cyrillic

If you have edgy issue:

sudo apt-get texlive-lang-cyrillic

If you have the manual install of texlive (not edgy) you may need to do a FULL install to get cyrillic fonts.

---

### Post by barmaley on 2006-12-05
I have installed texlive manually, following this howto.
I'm not that experienced in tex, threfore I do not mange to add fonts and I also don't know yet how to uninstall texlive.
If someone knows, please, help.

---

### Post by neoflight on 2006-12-05
> **barmaley said:**
> I have installed texlive manually, following this howto.
I'm not that experienced in tex, threfore I do not mange to add fonts and I also don't know yet how to uninstall texlive.
If someone knows, please, help.


if you have followed the howto then texlive will be installed in /usr/local/texlive

remove those folder and all inside it will essentially 'uninstall' texlive. undo the changes you made in the bashrc file too. 

You could install texlive from the repos. after enabling the appropriate repos (universe i guess) search for texlive in synaptic. you may also get the fonts from there...

uninstall is easy when you have installed it from the repos. Just  use synaptic. hope this helps

---

### Post by barmaley on 2006-12-06
Hello, ubuntu people.
Thanks for the help.

---

### Post by neoflight on 2006-12-07
if you have installed both texlive and texmaker from the repos, texmaker should work out of the box. make sure that you have the proper packages such as xdvi et al are installed. 

i tested this and have no problem compiling and viewing pdf docs with evince.  things are easier now. :)

---

### Post by Aramis on 2006-12-13
> **Aramis said:**
> [...]
Second of all, the technique describe to add packages to the LaTeX repository does not seem to work. I have a document that requires the use of the DROPPING package. I checked before following the intruction if the package was on my machine... after all TeXlive takes nearly 3GB, and I could see that the STY file was in the LaTeX folder. I tried to compile the file again... no luck. I followed the instructions, and still no luck. I would really appreciate some help here. I have done the texhash, and rehash. The file is where it should be... but for some reason it seems that TeXMaker (or indeed the command it uses to compile) cannot find it.


**Problem solved!!!!**

The author of the DROPPING packages writes in the documentation provided about DROPPING in tex-live that modern implementation of LaTeX such as pdflatex (which I use) might no longer work, and suggests to use the **lettrine** package instead [ [link]("http://www.tug.org/tex-archive/macros/latex/contrib/lettrine/doc/")  ] . I have tried it and it works with minor differences! In a nutshell, the letter immediately after the one(s) you chose to capitalise appears in small caps.

I hope that helps & Happy TeXing!

Ar@mi$

---

### Post by neoflight on 2006-12-28
changes made in the original post #1. info regarding new installation if you are using Edgy. Thanks.

---

