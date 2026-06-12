---
title: "Having troubles with KDevelop"
date: 2008-12-25
forum: Programming Talk
---

### Post by Arukas on 2008-12-25
I am trying to compile a hello work in program in Ubuntu with KDevelop using allegro.  Here's the link of the tutorial I used.  

[http://wiki.allegro.cc/index.php?title=KDevelop]("http://wiki.allegro.cc/index.php?title=KDevelop")


When I click the build project, I have what it means, and haven't been able to find someone who does.  Any help would be appreicated.  I just click "Run them"

[PHP]
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?
[/PHP]

Then the compilers spits out a sanity check literally.

[PHP]cd '/home/revenant/Code Projects/Vista/vista' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && cd '/home/revenant/Code Projects/Vista/vista/debug' && CXXFLAGS="-O0 -g3" "/home/revenant/Code Projects/Vista/vista/configure" --enable-debug=full && cd '/home/revenant/Code Projects/Vista/vista/debug/./src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k vista
aclocal
autoheader
automake
autoconf
installing -c
configure: error: ls -t appears to fail. Make sure there is not a broken
alias in your environment
configure: error: newly created file is older than distributed files!
Check your system clock
checking whether build environment is sane... 
*** Exited with status: 1 ***[/PHP]





Needless Ranting:
Okay, yet again, KDevelop is giving me a problem.  I begining to think that programming in Ubuntu is pointless.  I can download free windows compilers with IDE and get them to work with no problem.  Why doesn't anything work with Ubuntu?  Anguta, Geany will compile but don't run.  I wanting something better than gedit, terminal, and gcc

---

### Post by Arukas on 2008-12-28
Does anyone even use Kdevelop?  I think my first problem was because of the directory name, had a space in it.  I have a new problem too.

I compiled a simple KDE hello world program and the compiler spit this back at me.  

What does theis mean? acinclude.m4:3724: the serial number must appear before any macro definition



[PHP]
cd '/home/revenant/Alexandria/Code/Vista2/Vista2' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && cd '/home/revenant/Alexandria/Code/Vista2/Vista2/debug' && CXXFLAGS="-O0 -g3" "/home/revenant/Alexandria/Code/Vista2/Vista2/configure" --enable-debug=full && cd '/home/revenant/Alexandria/Code/Vista2/Vista2/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** automake (GNU automake) 1.10.1 found.
*** Creating acinclude.m4
*** Creating list of subdirectories
cd . && make -f admin/Makefile.common subdirs
*** Creating configure.files
*** Creating configure.in
cd . && make -f admin/Makefile.common configure.in ;
*** Creating aclocal.m4
acinclude.m4:3724: the serial number must appear before any macro definition
acinclude.m4:3769: the serial number must appear before any macro definition
acinclude.m4:3814: the serial number must appear before any macro definition

[/PHP]

---

### Post by dishmanw on 2009-01-07
I've been having problems compiling in KDevelop also.
I think I followed the same instruction that you did too.
It appears that they are missing a few steps.
When I first tried to build my program, there was no makefile.  
When I finally got it to start generating a makefile, I got an error saying that /.lib did not exist.
Does anyone have any better step by step instructions?

Right now, I'm just using KDevelop to edit my programs, and then I compile my program from the command-line.

   gcc program.c -o program -lalleg-4.2.1

"-lalleg-4.2.1" is the Allegro library.  This can very depending on the version.  So you should execute the following command to find the proper library.

   allegro-config --libs 


Or you can combine both of the above commands.

   gcc program.c -c program `allegro-config --libs`

Use the "`" symbol on the same key as the "~".  The single quote won't work.

---

### Post by Simian Man on 2009-01-07
If you are used to Visual Studio, I highly recommend Code::Blocks.  It works similarly and should be simpler for you.

---

### Post by Arukas on 2009-01-08
I get that alot, when I ask about KDevelop or Antuga, I people always suggest code::blocks.  I don't think any uses KDevelop at all.

---

