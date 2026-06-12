---
title: "Compiling and installing programs"
date: 2012-08-02
forum: Packaging and Compiling Programs
---

### Post by tempore on 2012-08-02
I'm trying to compile and install the program []("http://en.wikibooks.org/wiki/Grsecurity/Obtaining_grsecurity#Downloading_gradm")[gradm]("http://en.wikibooks.org/wiki/Grsecurity/The_Administration_Utility") and it is exiting with error 1, cannot open device /dev/grsec.

When I open the make file the variable DESTDIR is not defined. When I define it with / it compiles but the program does not run.

Google can't find anyone with a similar problem. (Or my Google-fu stinks)

From the Makefile
```

##############################################################################
# gradm (c) 2002-2011 - Brad Spengler, Open Source Security Inc.             #
# http://www.grsecurity.net                                                  #
#----------------------------------------------------------------------------#
# gradm is licensed under the GNU GPL v2 or higher http://www.gnu.org        #
##############################################################################

GRADM_BIN=gradm
GRADM_PAM=gradm_pam
GRSEC_DIR=/etc/grsec

LLEX=/usr/bin/lex
FLEX=/usr/bin/flex
LEX := $(shell if [ -x $(FLEX) ]; then echo $(FLEX); else echo $(LLEX); fi)
LEXFLAGS=-B
#ubuntu broke byacc for who knows why, disable it
#BYACC=/usr/bin/byacc
BISON=/usr/bin/bison
#YACC := $(shell if [ -x $(BYACC) ]; then echo $(BYACC); else echo $(BISON); fi)
YACC=$(BISON)
MKNOD=/bin/mknod
#for dietlibc
#CC=/usr/bin/diet /usr/bin/gcc
CC=/usr/bin/gcc
FIND=/usr/bin/find
STRIP=/usr/bin/strip
LIBS := $(shell if [ "`uname -m`" != "sparc64" -a "`uname -m`" != "x86_64" ]; then echo "-lfl" ; else echo "" ; fi)
OPT_FLAGS := $(shell if [ "`uname -m`" != "sparc64" ] && [ "`uname -m`" != "x86_64" ]; then echo "-O2" ; else echo "-O2 -m64" ; fi)
CFLAGS := $(OPT_FLAGS) -Wcast-qual -DGRSEC_DIR=\"$(GRSEC_DIR)\" -D_LARGEFILE64_SOURCE
LDFLAGS=
INSTALL = /usr/bin/install -c

# FHS
MANDIR=/usr/share/man
# older MANDIR
#MANDIR=/usr/man
DESTDIR=

OBJECTS=gradm.tab.o lex.gradm.o learn_pass1.tab.o learn_pass2.tab.o \
    fulllearn_pass1.tab.o fulllearn_pass2.tab.o fulllearn_pass3.tab.o \
    gradm_misc.o gradm_parse.o gradm_arg.o gradm_pw.o gradm_opt.o \
    gradm_cap.o gradm_sha256.o gradm_adm.o gradm_analyze.o gradm_res.o \
    gradm_human.o gradm_learn.o gradm_net.o gradm_nest.o gradm_pax.o \
    gradm_sym.o gradm_newlearn.o gradm_fulllearn.o gradm_lib.o \
    lex.fulllearn_pass1.o lex.fulllearn_pass2.o \
    lex.fulllearn_pass3.o lex.learn_pass1.o lex.learn_pass2.o \
    grlearn_config.tab.o lex.grlearn_config.o gradm_globals.o \
    gradm_replace.o

```
Make
```
gradm2$ make
/usr/bin/bison -b gradm -p gradm -d ./gradm.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm.tab.o gradm.tab.c
/usr/bin/flex -B -Pgradm ./gradm.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.gradm.o lex.gradm.c
/usr/bin/bison -b learn_pass1 -p learn_pass1 -d ./gradm_learn_pass1.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o learn_pass1.tab.o learn_pass1.tab.c
/usr/bin/bison -b learn_pass2 -p learn_pass2 -d ./gradm_learn_pass2.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o learn_pass2.tab.o learn_pass2.tab.c
/usr/bin/bison -b fulllearn_pass1 -p fulllearn_pass1 -d ./gradm_fulllearn_pass1.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o fulllearn_pass1.tab.o fulllearn_pass1.tab.c
/usr/bin/bison -b fulllearn_pass2 -p fulllearn_pass2 -d ./gradm_fulllearn_pass2.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o fulllearn_pass2.tab.o fulllearn_pass2.tab.c
/usr/bin/bison -b fulllearn_pass3 -p fulllearn_pass3 -d ./gradm_fulllearn_pass3.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o fulllearn_pass3.tab.o fulllearn_pass3.tab.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_misc.o gradm_misc.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_parse.o gradm_parse.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_arg.o gradm_arg.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_pw.o gradm_pw.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_opt.o gradm_opt.c
gradm_opt.c: In function &#8216;expand_acls&#8217;:
gradm_opt.c:53:14: warning: ignoring return value of &#8216;readlink&#8217;, declared with attribute warn_unused_result [-Wunused-result]
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_cap.o gradm_cap.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_sha256.o gradm_sha256.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_adm.o gradm_adm.c
gradm_adm.c: In function &#8216;start_grlearn&#8217;:
gradm_adm.c:366:3: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result [-Wunused-result]
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_analyze.o gradm_analyze.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_res.o gradm_res.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_human.o gradm_human.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_learn.o gradm_learn.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_net.o gradm_net.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_nest.o gradm_nest.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_pax.o gradm_pax.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_sym.o gradm_sym.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_newlearn.o gradm_newlearn.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_fulllearn.o gradm_fulllearn.c
gradm_fulllearn.c: In function &#8216;output_learn_header&#8217;:
gradm_fulllearn.c:485:2: warning: format not a string literal and no format arguments [-Wformat-security]
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_lib.o gradm_lib.c
/usr/bin/flex -B -Pfulllearn_pass1 ./gradm_fulllearn_pass1.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.fulllearn_pass1.o lex.fulllearn_pass1.c
/usr/bin/flex -B -Pfulllearn_pass2 ./gradm_fulllearn_pass2.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.fulllearn_pass2.o lex.fulllearn_pass2.c
/usr/bin/flex -B -Pfulllearn_pass3 ./gradm_fulllearn_pass3.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.fulllearn_pass3.o lex.fulllearn_pass3.c
/usr/bin/flex -B -Plearn_pass1 ./gradm_learn_pass1.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.learn_pass1.o lex.learn_pass1.c
/usr/bin/flex -B -Plearn_pass2 ./gradm_learn_pass2.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.learn_pass2.o lex.learn_pass2.c
/usr/bin/bison -b grlearn_config -p grlearn_config -d ./grlearn_config.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o grlearn_config.tab.o grlearn_config.tab.c
/usr/bin/flex -B -Pgrlearn_config ./grlearn_config.l
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o lex.grlearn_config.o lex.grlearn_config.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_globals.o gradm_globals.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE   -c -o gradm_replace.o gradm_replace.c
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE -o gradm gradm.tab.o lex.gradm.o learn_pass1.tab.o learn_pass2.tab.o fulllearn_pass1.tab.o fulllearn_pass2.tab.o fulllearn_pass3.tab.o gradm_misc.o gradm_parse.o gradm_arg.o gradm_pw.o gradm_opt.o gradm_cap.o gradm_sha256.o gradm_adm.o gradm_analyze.o gradm_res.o gradm_human.o gradm_learn.o gradm_net.o gradm_nest.o gradm_pax.o gradm_sym.o gradm_newlearn.o gradm_fulllearn.o gradm_lib.o lex.fulllearn_pass1.o lex.fulllearn_pass2.o lex.fulllearn_pass3.o lex.learn_pass1.o lex.learn_pass2.o grlearn_config.tab.o lex.grlearn_config.o gradm_globals.o gradm_replace.o  
Unable to detect PAM headers, disabling PAM support.
/usr/bin/bison -b grlearn2_config -p grlearn2_config -d ./grlearn2_config.y
/usr/bin/gcc -O2 -m64 -Wcast-qual -DGRSEC_DIR=\"/etc/grsec\" -D_LARGEFILE64_SOURCE -DIS_GRLEARN -o grlearn grlearn.c gradm_lib.c gradm_globals.c grlearn2_config.tab.c lex.grlearn_config.c 

```

make install
```

gradm2$ sudo make install
Installing gradm...
Installing grlearn...
Installing gradm manpage...
Could not open /dev/grsec.
open: No such device or address

make: *** [install] Error 1

```

---

### Post by Cheesemill on 2012-08-02
Are you using a grsecurity patched kernel?

From the very top of the page you linked to:
> Before you install gradm, boot into your patched grsecurity kernel. You can compile gradm in any kernel you wish, but the installation will fail if the kernel does not support grsecurity.

---

### Post by tempore on 2012-08-02
Yes, the kernel has been compiled successfully. 
```

$ uname -a
Linux c 3.2.24-grs-grsec #1 SMP PREEMPT Wed Aug 1 18:08:14 EDT 2012 x86_64 x86_64 x86_64 GNU/Linux

```And I have a /dev/grsec

Do you know if I should worry about the warnings during make?

---

### Post by oldos2er on 2012-08-02
Moved to Packaging and Compiling Programs.

---

### Post by tempore on 2012-08-02
I was really hoping for the exposure of the beginner forum. And, after all, I'm a beginner. :)

---

### Post by Rallg on 2012-08-02
Compiling is not for beginners. :guitar:

Normally, you do not need to worry about "warnings" during make. Many, maybe all, of those messages merely indicate that something is unexpected but not serious, or might be a problem IF you use the resulting program in a certain way. Almost always, the warning cannot be resolved except by editing the program code (C++ or whatever). That's not your job. I have successfully used programs that generate numerous warnings during compile.

I am not familiar with the program you are compiling. But it seems to me that /dev/grsec is an unusual location. Check the source code INSTALL file (if it has one) to see if there is advice.

---

### Post by tempore on 2012-08-02
There is no INSTALL file however there is a README that isn't very helpful.

[[url=http://forums.grsecurity.net/viewtopic.php?f=3&t=1570]This]("http://%22http://forums.grsecurity.net/viewtopic.php?f=3&t=1570") [/URL]link would seem to help even though it is from 6 years ago.
```

make install' places vmlinuz in / instead of /boot/.

```I compiled the kernel importing the .config file with instructions found [here.]("http://www.howtoforge.com/kernel_compilation_ubuntu") I made minimal adjustments to the menuconfig. But the kernel compiled, installed and I'm running it! I installed the kernel from the /usr/src directory with dpkg - not sure if that matters.

Anyway thanks for your help. Any nudge in the right direction is appreciated!

---

