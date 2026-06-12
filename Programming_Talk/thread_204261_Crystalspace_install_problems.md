---
title: "Crystalspace install problems"
date: 2006-06-26
forum: Programming Talk
---

### Post by mighk on 2006-06-26
Hi 
I have downloaded crystal space manually installed it, it appears under installed programs but i can't seem to start it,no icons, no go !  any advice please.
thanks 
mighk

---

### Post by Druke on 2007-08-20
crystalspace doesn't work like that, try typing 'walktest' on a terminal or in 'alt f2' . After you confirm that its there, proceed to the cs website and read more there 

:popcorn: for choosing CS

---

### Post by elfostens on 2010-04-16
Hey there,

i'm not sure if it is the right place for this posting but i don't know where to post it anywhere. I got following problem, i installed crystalspace using synaptic paket manager, i installed the crystalspace dev pakage the standard pakage and the doc. Then i just wanted to continue with CEL also some crystalspace stuff. So i downloaded the tar.bz2 file, unziped and untar-ed it. Already was fine. I had to do it manually because there were no pakages in synaptic pakage manager.  so fine so far ...
when i hit ./configure in the command line, while beeing in the cel directory, the following lines ran down the console ...

```
./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether to enable -mno-cygwin... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking if gcc accepts -pipe... -pipe
checking if gcc handles Sparc v9... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to treat C++ warnings as errors... no
checking how to enable C++ PIC generation... no
checking for ld... ld
checking if binutils version >= 2.17... yes (version 2.20)
checking if -shared is accepted... no
checking if -soname is accepted... no
checking if response files are accepted... no
checking if --as-needed is supported... no
checking if --no-as-needed is supported... no
checking if --gc-sections is supported... no
checking for ranlib... ranlib
checking for dlltool... no
checking for dllwrap... no
checking for windres... no
checking for strings... strings
checking for objcopy... objcopy
checking for libtool... no
checking for glibtool... no
checking for gnulibtool... no
checking for libtool... no
checking how to create a directory... mkdir
checking how to create a directory tree... mkdir -p
checking for install... install
checking whether ln -s works... yes
checking for texi2dvi... no
checking for texi2pdf... no
checking for dvips... no
checking for dvipdf... dvipdf
checking for makeinfo... no
checking for doxygen... no
checking for dot... no
checking for rsvg... no
checking for icotool... no
checking for convert... no
checking for perl5... no
checking for perl... perl
checking for perl5... (cached) perl
checking for TemplateToolkit... no
checking for ttree... no
checking for swig... no
checking how to enable C++ compilation warnings... no
checking how to suppress C++ unused variable warnings... no
checking how to suppress C++ uninitialized variable warnings... no
checking for flag to disable string-aliasing... no
./configure: line 9133: test: !=: unary operator expected
checking if binutils version >= 2.16... yes (version 2.20)
checking whether to split debug information... yes
checking how to enable debug mode debugging symbols... no
checking whether to enable debug information in optimize mode... yes
checking how to enable optimize mode debugging symbols... no
checking how to treat C warnings as errors... -Werror
checking how to treat C++ warnings as errors... no
checking for STL... no
checking how to treat C++ warnings as errors... (cached) no
checking how to enable C++ PIC generation... (cached) no
checking for inline visibility flag... no
checking for hidden symbol visibility flag... -fvisibility=hidden
checking for pthread... yes
checking for pthread recursive mutexes... PTHREAD_MUTEX_RECURSIVE
checking how to suppress C++ `long double' warnings... no
checking for python... python
checking for python SDK... yes
checking if python SDK is usable... no
checking for pkg-config... pkg-config
checking if pkg-config recognizes cppunit... no
checking for cppunit-config... no
checking for libcppunit... no
checking for pthread... (cached) yes
checking for pthread recursive mutexes... (cached) PTHREAD_MUTEX_RECURSIVE
checking if pkg-config recognizes NL... no
checking for NL-config... no
checking for libNL... no
checking for cs-config-1.1... no
checking for cs-config-1.2... no
checking for cs-config-1.4... /usr/bin/cs-config-1.4
checking if Crystal Space version >= 1.1... yes (version 1.4.0)
checking if Crystal Space SDK is usable... no
configure: error:
*** Crystal Space could not be found or was unusable. The latest version is
*** always available from http://www.crystalspace3d.org/
*** Also, be sure that you have either installed Crystal Space or set the
*** CRYSTAL environment variable properly.
```

so spend an unbelievable view at this kinda Oo, you know.

I already intalled everything its needed for crystalspace including crystalspace and then such a failure message ... kinda annoying ...

Could it be that i have to set a pathline in some files or such thing like that. the Walktest works fine, and i've searched my system directories, crystalspace seems to be installed, it'S a little bit scattered over a lot of directories but it's there and still functioning. But the ./configure routine doesn'T find it ...

any tipps out there??

I don'T want to deinstall crystalspace and try installing it manually but if this should be the only way to get it work ... i have to .

Thanks for any advices.

---

### Post by Druke on 2010-04-16
I HIGHLY recommend you don't mix debs and other things with this.

In fact, if you're planning on programming with it, you're going to want to install it locally.

What I do is set up `~/Documents/lib` and then grab teh source for CS and do a configure --prefix=~/Documents/lib/CS



But to your specific error: you haven't set the CRYSTAL env variable. You should pop into #crystalspace on freenode irc, they're friendly :).

---

### Post by elfostens on 2010-04-16
Thanks for this advice, i will check out the irc.:popcorn:

But i still keep an eye to this thread, perhaps anyone has an idea where to set this CRYSTAL enviroment variable or has another clue to a solution ;)

---

### Post by elfostens on 2010-04-20
so far so good ...

i got some not so "new" informations from irc.freenode.net #CrystalSpace. they meant, i should set some CRYSTAL=/root/dir/of/CS and perhaps an LD_LIBRARY_PATH=/install/path/of/CS variables. I've checked the directories and realized that synaptic package manager installed the whole CrystalSpace stuff in different directories, so there isn'T a real root dir of CS. It seems that i have to set more variables than just these 2. Next problem is i don'T know where or in which file i have to set those variables. Perhaps in .bashrc file? Don'T really know. The Guys from the #CrystalSpace room also can'T or didn'T want to tell me the correct file where to set these variables. 

Perhaps you got an clue? I'm still trying to fix that without a manually installation of CrystalSpace.

kind regards,

elfostens.

---

### Post by baldmenace on 2010-06-04
you have to use export .. which is supose to mod you path similar to path% = path but having similar issues.. 
 so 
you have to type in terminal 
export LD_LIBRARY_PATH=/home/crystalspace1.4.0/
sudo ldconfig
that will set the path so that it can find the lib file

---

