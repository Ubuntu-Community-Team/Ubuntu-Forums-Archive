---
title: "tclConfig.sh, tkConfig.sh"
date: 2008-06-23
forum: Programming Talk
---

### Post by swordsmith on 2008-06-23
Hi all,
I'm trying to install WordNet on Gutsy, I have both tcl and tk installed, however, ./configure returns this error:

allen@Swordforge:~/Desktop/WordNet-3.0$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for strchr... yes
checking for strdup... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for nl_langinfo and CODESET... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for Tcl configuration... configure: WARNING: Can't find Tcl configuration definitions

I'm sure I have both tk and tcl, but I just cant find the respective config.sh files:

allen@Swordforge:~/Desktop/WordNet-3.0$ whereis tcl
tcl: /usr/lib/tcl8.4
allen@Swordforge:~/Desktop/WordNet-3.0$ whereis tclconfig
tclconfig:
allen@Swordforge:~/Desktop/WordNet-3.0$ whereis tk
tk: /usr/lib/tk8.4 /usr/share/tk8.4
allen@Swordforge:~/Desktop/WordNet-3.0$ whereis tkconfig
tkconfig:
allen@Swordforge:~/Desktop/WordNet-3.0$ 

Can anyone please help?

Thank you very much!

---

### Post by lloyd_b on 2008-06-24
It sounds like you have the library package installed, but not its corresponding development package.  Many libaries are split into two pieces, with the first being the stuff required to run programs using the library, and the second being the stuff required to compile programs that use the library.

In this case, try installing the packages "tcl8.4-dev" and "tk8.4-dev", and see if that resolves the issue.

Lloyd B.

---

### Post by HeresJohnny on 2008-11-15
Hi guys,

I was having problems with this as well, and I figured out that it is in the repos in Intrepid (and, I believe, in earlier iterations as well).  I felt pretty dumb when I just looked it up in Synaptic (after spending a long time running into the same problems as the first poster) and installed it.  Hope this helps!

---

### Post by cmodel on 2010-04-26
I have met this issue too.
but after I read the INSTALL and ./configure --help, it's solved then.

firstly, please check where is your tcl/tk,
using
$ whereis tcl
$ whereis tk

if there you have both, like tcl8.4/tk8.4, you will find
the location where they are, tipically they are
/usr/lib/tcl8.4,
/usr/include/tcl8.4, 
/usr/lib/tk8.4,
/usr/inclue/tk8.4,

then you will see under
/usr/lib/tcl8.4
/usr/lib/tk8.4
there have symbolic link of tclConfig.sh/tkConfig.sh

so when you perform the ./configure 
please use :
./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4

then configure will be done successfully.
after that, 
u can do &#65306;

make
make install


Till now, all is done for WordNet.
You can now enjoy your WordNet journey.

Hope it works.

---

### Post by ramrumram on 2010-06-18
This thing works for me perfectly

apt-get  install tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev

and then 


./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4

---

