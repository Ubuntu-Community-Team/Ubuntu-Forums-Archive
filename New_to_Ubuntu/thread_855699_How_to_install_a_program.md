---
title: "How to install a program"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by natman on 2008-07-10
I got this program - gyachi
[HTML]http://downloads.sourceforge.net/gyachi/gyachi-1.1.0.tar.gz?modtime=1194119273&big_mirror=0[/HTML]
( a linux IM client with voice well i hope anyway - not on adept)
Does anyone know how i go about installing it? It says its the platform indep. version i am using 64 bit Kubuntu

---

### Post by spiderbatdad on 2008-07-10
there is a deb for gyachi. search sourceforge for it...download it, click it. It self installs...get the plugins too.

---

### Post by oldos2er on 2008-07-10
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by spiderbatdad on 2008-07-10
look here:[http://sourceforge.net/project/showfiles.php?group_id=158490](http://sourceforge.net/project/showfiles.php?group_id=158490)

scroll down...find the deb packages.

---

### Post by natman on 2008-07-10
Ok what i did was extract the file then ran configure thing, and am left with
> natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ ls
ABOUT-NLS       config.h.in        depcomp         libtool        plugins
aclocal.m4      config.log         doc             ltmain.sh      po
audibles        config.rpath       gyachi.desktop  m4             smileys
autogen.sh      config.sub         gyachi.spec.in  Makefile.am    sounds
autom4te.cache  configure          gyvoice         Makefile.in    spec_files
ChangeLog       configure.ac       install-sh      missing        tuxvironments
client          configure.ac.tmpl  INSTALL.txt     mkinstalldirs  VERSION
config.guess    CVS                intl            pixmaps        webcam

in the directory, i think i am meant to run "make" but i have no idea what its argument is, every time i type make MAKEFILE.IN it just says nothing to be done. whats next?

---

### Post by fatality_uk on 2008-07-10
If you downloaded the *.deb, judt double clik that and it will isnatll it for you!

---

### Post by natman on 2008-07-10
I would love to but i am running 64 bit linux that deb is for 32 only. I also tried forcing the install still nothing, im stuck with the make config stuff

---

### Post by mister_pink on 2008-07-10
Firstly I recommend you just go with the deb options outlined above - you just double click and it installs!

However, if you're keen to learn how to compile software read on (and read that monkeyblog link above too).

You need to pay attention to the output of the ./configure command, if it gives any errors, especially "unmet dependencies". This is other software that you need to install before the compile will work.

Next "make" is run without any arguements (normally). This compiles the software. 

Finally you often need to do "make install" or often "sudo make install". This actually places the files in the right places and sets it up ready to use. You can sometimes do something like "make help" to see what the options are, or even open the makefile in a text editor and it will have the different options at the bottom.

Ok, so I just downloaded the source code and had a look. Did you read INSTALL.txt? That basically tells you what to do.

---

### Post by natman on 2008-07-10
Thanks PINK, seems ok but this is what i have
> natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ ls
ABOUT-NLS   autom4te.cache  config.h.in   configure          depcomp         gyvoice      libtool      Makefile.in    plugins  spec_files
aclocal.m4  ChangeLog       config.log    configure.ac       doc             install-sh   ltmain.sh    missing        po       tuxvironments
audibles    client          config.rpath  configure.ac.tmpl  gyachi.desktop  INSTALL.txt  m4           mkinstalldirs  smileys  VERSION
autogen.sh  config.guess    config.sub    CVS                gyachi.spec.in  intl         Makefile.am  pixmaps        sounds   webcam
natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ make gyachi.spec.in
make: Nothing to be done for `gyachi.spec.in'.
natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ make gyachi.spec.in
make: Nothing to be done for `gyachi.spec.in'.
natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ make
make: *** No targets specified and no makefile found.  Stop.
natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$ make install
make: *** No rule to make target `install'.  Stop.
natman@natman-laptop:~/Desktop/gyachi-1.1.0/gyachi-1.1.0$

Am i all done, what next? the INSTALL file is saying that make should do something?

---

### Post by oldos2er on 2008-07-10
If "make" isn't working, it means "configure" didn't work properly. Run ./configure again and post any error messages it shows.

---

### Post by natman on 2008-07-10
I have attached the whole output of ./configure, i think these are the oly problems
[HTML]./configure: line 31680: syntax error near unexpected token `ALSA,'
./configure: line 31680: `              PKG_CHECK_MODULES(ALSA, alsa >= 0.9.8)'
[/HTML]
But there are a whole load of bits that have "no" after them wheather these are things that just arnt needed for my set up i dont know, well there all in the attached file.
Thanks

---

### Post by oldos2er on 2008-07-11
Your problem is at the end:

checking for IceConnectionNumber in -lICE... no
./configure: line 31680: syntax error near unexpected token `ALSA,'
./configure: line 31680: `              PKG_CHECK_MODULES(ALSA, alsa >= 0.9.8)'

 I am not a programmer, but it looks like an error in the script, not a dependency problem. I'd try emailing the program's authors to see what they say.

 Much easier tho' to install the *.deb file, as has been suggested.

---

### Post by spiderbatdad on 2008-07-12
[http://ubuntuforums.org/showthread.php?t=773802](http://ubuntuforums.org/showthread.php?t=773802)

---

