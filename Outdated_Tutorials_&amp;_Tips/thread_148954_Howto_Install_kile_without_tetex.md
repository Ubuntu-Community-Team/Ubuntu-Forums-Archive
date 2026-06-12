---
title: "Howto: Install kile without tetex"
date: 2006-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by neoflight on 2006-03-23
Tips to install kile from the source without tetex....

Information for this comes from [kile]("http://kile.sourceforge.net/") webpage. 

Kile is an excellent frontend to be used with TeXLive (the most comprehensive LaTeX pack). But if you install it using apt-get or synaptic, tetex will also be installed. If you desire not to use tetex then this will help...

Actually, compiling from sourse is easy. But good to know what packages/libs we need to avoid running into problems. I thought I will share my experience with you...

Enable all the repositories required. If the installation was a fresh one then uncomment all the debs and deb-srcs..

First install all the libs needed for installing kile, tools for compiling and 'make' process, etc
```
sudo apt-get install build-essential kdelibs-bin kdebase-dev libqt3-mt-dev

```
These will bring many other libs with them that are required.

So we have all the tools now. Download the latest source [here]("http://kile.sourceforge.net/download.php")
unpack it and move
```
tar -jxf kile-1.9.tar.bz2
sudo mv kile-1.9 /usr/local
```
then
```
cd /usr/local/kile-1.9
```
Now the compiliation:
find out where the kde-config is, at the terminal
```
kde-config --prefix
```
do
```
./configure --prefix=/output/from/above
```
In my case it gave me '/usr'.
if it is successful then run 
```
make
sudo make install
```
It should be placed in Applications>Office. Or
Alt+F2 --> kile...will launch it...

This is just a reference...Eventhough it brings up many KDE stuff (I use Gnome), I felt its much better/space-saving than all the tetex installations. I use texlive, tips for which are provided in my signature.

Hope this is of some help...Thanks

---

### Post by sherlock-holmes on 2006-06-01
it certainly brings up problems when trying to do upgrades...!!! gnome user might get upset in updating all the kde stuff...

---

### Post by dada1958 on 2006-06-02
Tnx for this how to; the first attempt failed but that was my fault :)

---

### Post by maulattu on 2006-06-03
good ;)

---

### Post by neoflight on 2006-06-03
thanks a lot... i think its working ok with dapper....

---

### Post by maulattu on 2006-06-03
[QUOTE=neoflight]thanks a lot... i think its working ok with dapper....[/QUOTE]

yes, i'm using dapper8)

---

### Post by troy7777 on 2006-07-13
my solution was to install a dummy package that provides tetex. so you can install all the other packages that depends on tetex (like auctex) without installing tetex. then i installed TeXLive.

---

### Post by snl on 2006-07-14
I tried to install Kile following this howto but it always failed during the installation giving the following error 
```
trying to overwrite `/usr/share/apps/katepart/syntax/bibtex.xml', which is also in package kdelibs-data

```
Please help.

> **troy7777 said:**
> my solution was to install a dummy package that provides tetex. so you can install all the other packages that depends on tetex (like auctex) without installing tetex. then i installed TeXLive.

How do I install the dummy package?

Thank you.

---

### Post by troy7777 on 2006-07-14
> How do I install the dummy package?

 i got the instruction from this forum, too, a while back. it wasn't specifically tetex. unfortunately, i could not find the original post. so, credit goes to the original poster.

here's how i did it. i'm assuming you are doing all these in a terminal window.

1. you need to install the equivs package. i think it's in universe, so activate the necessary line in your sources.list file. then do:

```
sudo apt-get install equivs
```

2. create a text file called tetex-dummy.control and put the following:

```
Section: TeX Authoring
Package: tetex-dummy
Provides: tetex-base, tetex-bin, tetex-extra, tetex-doc, tetex-extra, tex-common
Description: Dummy package for tetex so that TeXLive can be installed.
```

3. create the package.

```
equivs-build tetex-dummy.control
```

this will create, among other things, a tetex-dummy-xxx.deb

4. install the deb file you created:

```
sudo dpkg -i tetex-dummy-xxx.deb
```

5. install kile and TeXLive!

hope this helps.

---

### Post by neoflight on 2006-07-16
> **troy7777 said:**
> i got the instruction from this forum, too, a while back. it wasn't specifically tetex. unfortunately, i could not find the original post. so, credit goes to the original poster.

here's how i did it. i'm assuming you are doing all these in a terminal window.

1. you need to install the equivs package. i think it's in universe, so activate the necessary line in your sources.list file. then do:

```
sudo apt-get install equivs
```

2. create a text file called tetex-dummy.control and put the following:

```
Section: TeX Authoring
Package: tetex-dummy
Provides: tetex-base, tetex-bin, tetex-extra, tetex-doc, tetex-extra, tex-common
Description: Dummy package for tetex so that TeXLive can be installed.
```

3. create the package.

```
equivs-build tetex-dummy.control
```

this will create, among other things, a tetex-dummy-xxx.deb

4. install the deb file you created:

```
sudo dpkg -i tetex-dummy-xxx.deb
```

5. install kile and TeXLive!

hope this helps.

excellent....i will try this and will let u know.....it might be a better idea than compiling from the source... thanks

---

### Post by neoflight on 2006-07-16
> **snl said:**
> I tried to install Kile following this howto but it always failed during the installation giving the following error 
```
trying to overwrite `/usr/share/apps/katepart/syntax/bibtex.xml', which is also in package kdelibs-data

```
Please help.

Thank you.

actually i dont know what happened here? is it a permission problem? 
may be removing it and reinstalling helps?

---

### Post by kozimodo on 2006-07-16
Kile does not seem to want to play with TexLive.  When I type "tex --version" in a terminal window, I get the expected output but if I try to compile a document, it says that it can't find LaTex.  The Kile "system check" gives me an error for everything.

What am I doing wrong?

---

### Post by snl on 2006-07-17
Thank you troy7777 and neoflight for your helps.

---

### Post by neoflight on 2006-07-18
> **kozimodo said:**
> Kile does not seem to want to play with TexLive.  When I type "tex --version" in a terminal window, I get the expected output but if I try to compile a document, it says that it can't find LaTex.  The Kile "system check" gives me an error for everything.

What am I doing wrong?

i guess i know the answer.... texlive and kile are installed...

now go to the kile settings>configure kile> tools>build...

enter the entire path to the latex commands....

for eg. if you have installed texlive at the default location specified by texlive...then it would look like...
```
/usr/local/texlive/2005/bin/i386-linux/<command>
```
see the screenshots...

in the second one: see the 'run outside of kile' setting....so you are telling kile to use the commands you want and so the location.

before doing so ...run texconfig as root from the terminal.. then do the system check and see whether you get any errors... some errors can be neglected...foreg: viewing dvi files using the type u want...kile might suggest something....technically giving the whole path to the command should work. 

its better to use a sample latex code and check rather than using the system check....make sure that you have installed the applications before checking...for eg...install acroread or evince or similar pdf viewer before you can ask kile to open the pdf....

let me know if it works for u .... good luck...

---

### Post by kozimodo on 2006-07-19
Thanks!  I have nearly everything working now -- one other issue is how to get kdvi working (I like it because it can be run embedded in Kile).  It looks for kpsewhich which is no longer in the expected location.  I haven't been able to find how to tell kdvi where to look.

---

### Post by Sam D on 2006-08-01
Sorry for this basic question : what is tetex and why is it not necessary ?

Furthermore, why could we only get kile1.8 from the depository ? I've heard that kile1.9 has some real improvements...

I've also read that tetex is not maintained any longer. What are the implications ?

---

### Post by jordilin on 2006-08-01
> **kozimodo said:**
> Kile does not seem to want to play with TexLive.  When I type "tex --version" in a terminal window, I get the expected output but if I try to compile a document, it says that it can't find LaTex.  The Kile "system check" gives me an error for everything.

What am I doing wrong?

Take a look at my howto here:
[http://jordilin.wordpress.com/2006/07/31/howto-installing-and-compiling-the-latest-latex-and-kile-packages/](http://jordilin.wordpress.com/2006/07/31/howto-installing-and-compiling-the-latest-latex-and-kile-packages/) 
or here:
[http://www.ubuntuforums.org/showthread.php?t=226332](http://www.ubuntuforums.org/showthread.php?t=226332)

You will only need to put the next line in your .bashrc:
```
PATH=$PATH:/usr/local/texlive/2005/bin/i386-linux
```

---

### Post by jordilin on 2006-08-01
> **Sam D said:**
> Sorry for this basic question : what is tetex and why is it not necessary ?

Furthermore, why could we only get kile1.8 from the depository ? I've heard that kile1.9 has some real improvements...

I've also read that tetex is not maintained any longer. What are the implications ?

Tetex is a tex distribution for Unix like systems. Tetex is no longer mantained, but there are other ways to install a tex system in your computer. Read the howto:
[http://www.ubuntuforums.org/showthread.php?t=226332](http://www.ubuntuforums.org/showthread.php?t=226332)

---

### Post by Sam D on 2006-08-01
Bale, bale. Gracias by the way for your post I already red.
The point is that I don't feel like installing things that I can't remove easily. If there is a package, I can use debfoster to remove it in a clean manner. ;) 

So, back to my question : why the Ubuntu communauty does not seem to be interested by an updated Kile (or equivalent, if there is... I guess Kile is one of the best for non-emacs-fluent-people) ?

I know nothing about how to make a package, but if there is someone that is able to do what you proposed in a nice package and add it to the repository, it would be great ! :cool:

---

### Post by anders_jel on 2006-10-29
Texlive from the repositories unfortunatly conflicts with the tetex dummy package. To get kile working with texlive without compiling kile from sources:

1. Get the kile deb file from [http://packages.ubuntulinux.org/edgy/tex/kile]("http://packages.ubuntulinux.org/edgy/tex/kile")

2. Open a console and go to the location of the file

3. dpkg-deb -x kile_versionStuff.deb kile_versionStuff

4. dpkg-deb -e kile_versionStuff.deb kile_versionStuff/DEBIAN

5. Go to the kile_versionStuff/DEBIAN folder and open the control file using your favorite text editor

6. Change the package name from kile to kile-texlive

7. Change the dependency tetex-bin to texlive-base

8. Optional: Remove tetex stuff from recommends and add texlive and texlive-full instead

9. Add ", kile" to conflicts so you do not accidentially install kile on top of kile-texlive

10. Save the file and go back to the console and to the directory you started with (where you have the deb file).

11. mv kile_versionStuff kile-texlive_versionStuff

12. dpkg-deb -b kile-texlive_versionStuff kile-texlive_versionStuff.deb

13. dpkg -i kile-texlive_versionStuff.deb

14. If there are dependency problems open you favorite package manager and solve them, remove the broken kile-texlive package and go to step 13.

---

### Post by jbor7755 on 2007-06-20
Okay so now that I cannot acces any help through kile or access any english dictionaries (and since it is easier and safer to intstall from the repositories), how can I uninstall it?

You can't use apt or synaptic or dpkg because it was compiled from source code!!!

---

### Post by Despot Despondency on 2008-08-18
Great HowTo, all worked fine for me. I usually find compiling from source a complete nightmare, so this really saved me a lot of effort.:)

---

### Post by fmang on 2008-11-14
I'm trying to follow this HowTo using Kile v2.0.2 but I can't seem to install it.

when I go to the /usr/loca/kile-2.0.2/ directory and after invoking ```
kde-config --prefix
``` I get ```
/usr
``` then after ```
./configure --prefix=/usr
``` what I get is a long stream of messages that end in this error ```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!

``` Please help! I already installed KDE, removed it and installed it again but it's no use. I'm using Ubuntu 8.10

---

### Post by gokbektas on 2009-01-16
I've exactly the same problem

```

kde-config --prefix
/usr
```


```
./configure --prefix=/usr
.
.
.
.
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```


Ubuntu 8.10

KDE is under usr/include/KDE as default.


What's wrong?

---

### Post by utdream on 2009-01-16
I got my compile (of a different app - twinkle) working past this issue by installing the kdelibs4-dev package. This removed some other conflicting kde libs but it did get me past this particular issue.

I got the idea from the kubuntu forum here:

[http://kubuntuforums.net/forums/index.php?topic=3098493.0](http://kubuntuforums.net/forums/index.php?topic=3098493.0)

HTH anyone else who runs into this problem.

---

