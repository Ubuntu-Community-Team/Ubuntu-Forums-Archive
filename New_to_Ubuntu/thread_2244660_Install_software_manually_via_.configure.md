---
title: "Install software manually via ./configure?"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by Sword90 on 2014-09-17
Hello all,
I am actually not a new Ubuntu user but this seemed to be the appropriate category to create the topic.
How to install .deb packages and .sh installation is obviously very easy.
For the last 2 or so years I always had trouble to install from a .tar.gz source.
The procedure to install via ./configure and so on and so forth is obvious but most times there are dependencies missing. 
For example I was about to install a program (cinepaint) today and got this output

> 
    Configuration Results

GTK CinePaint Version 1.0-4


General dependencies:
   Gtk2 toolkit                 yes    
   DnD support                  no
   littleCMS                    no     !! CinePaint will not build without !!
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             no     !! CinePaint will not build without !!
   Tiff plug-in:                no     !! CinePaint will not build without !!
   PNG plug-in:                 no
   Jpeg plug-in:                no     !! CinePaint will not build without !!
   Print plug-in:               no
   FLTK dependent plug-ins:     no     !! CinePaint will not build without !!
   Thread dependent plug-ins:   no     !! ICC Examin will not build !!
   Flex dependent plug-ins:     no
=================================================================

configure: error: !!! An ERROR occured !!!
    Please check the above messages to see why.
    For bug reports please include the complete above output.


It does not say which names the dependency packages have and also the INSTALL file does not always help. This Program Cinepaint now was just an example so I do not need an explicit explanation how to install it, I want to know in general what do I have to do if the worst case happens -> ./configure tells you dependencies are missing and the INSTALL file does not help you.
What do I have to do in that case?

This bothers me for many years and I have never been able to find a solution :/

Thank you all in advance :-)

---

### Post by claracc on 2014-09-18
About how to install cinepaint from source, fixing missing dependencies, I have found this thread:
[http://ubuntuforums.org/showthread.php?t=2156330](http://ubuntuforums.org/showthread.php?t=2156330) where there is a complete and clear explanation on how to resolve missing dependencies with cinepaint, please, pay special attention to comments #2 and #13.

About solving missing dependencies when trying to install other software from source, each case is different, dependency software packages are differente but after running ./configure you obtain clues about what software is needed and as mc4man points, to search it with synaptic and trying to install. In comment number #2 of forementioned thread is given also a procedure which can work for other packages.

---

### Post by oldos2er on 2014-09-18
> **Sword90 said:**
>  This Program Cinepaint now was just an example so I do not need an explicit explanation how to install it, I want to know in general what do I have to do if the worst case happens -> ./configure tells you dependencies are missing and the INSTALL file does not help you.
What do I have to do in that case?

You search the repositories using the search terms given you by the terminal output you showed us, for example, given ```
General dependencies:
   Gtk2 toolkit                 yes    
   DnD support                  no
   littleCMS                    no     !! CinePaint will not build without !!
   Oyranos                      no
``` I would run ```
apt-cache search littleCMS
``` which gives me ```
liblcms2-2 - Little CMS 2 color management library
liblcms2-dev - Little CMS 2 color management library development headers
liblcms-utils - Little CMS color management library utilities
liblcms1 - Little CMS color management library
liblcms1-dev - Litle CMS color management library development headers
liblcms2-utils - Little CMS 2 olor management library
python-liblcms - Python bindings for Little CMS color management library
``` Knowing I need -dev files in order to compile, I would then install liblcms2-dev, rerun ./configure and see if it works. Repeat this process for each dependency.

Sometimes dependencies will be listed in a README file distributed with the source code, or they will be shown on the program's home page if it has one.

More info: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

There's also a specific [subforum]("http://ubuntuforums.org/forumdisplay.php?f=44") for help with compiling software, since it's not an activity that's popular with most "new to Ubuntu" folks.  :)

---

