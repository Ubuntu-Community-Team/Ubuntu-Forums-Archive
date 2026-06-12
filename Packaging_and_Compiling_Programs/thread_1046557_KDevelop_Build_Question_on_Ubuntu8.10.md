---
title: "KDevelop Build Question on Ubuntu8.10"
date: 2009-01-21
forum: Packaging and Compiling Programs
---

### Post by flylehe on 2009-01-21
Hi,
I built a very simple c project in KDevelop on my Ubuntu8.10 but recieved the following error. I cannot figure out why. Thanks for your help!

"cd '/home/tli/program/eg1_KDe/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
make all-recursive
Making all in src
compiling eg1.c (gcc)
mv -f .deps/eg1.Tpo .deps/eg1.Po
linking eg1_kde (CC)
../libtool: line 818: X--tag=CC: command not found
../libtool: line 851: libtool: ignoring unknown tag : command not found
../libtool: line 818: X--mode=link: command not found
../libtool: line 985: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 986: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 2223: X-O0: command not found
../libtool: line 2223: X-g3: command not found
../libtool: line 2392: Xeg1_kde: command not found
X: user not authorized to run the X server, aborting.
../libtool: line 2404: Xeg1_kde: command not found
../libtool: line 2412: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make[2]: *** [eg1_kde] Error 1
make[2]: Target `all' not remade because of errors.
make[2]: Nothing to be done for `all-am'.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***
"

---

### Post by blackpix on 2009-03-09
I have got the same problem.

---

### Post by articfox on 2009-05-01
Try this thread: [http://ubuntuforums.org/showthread.php?t=945424&highlight=kdevelop+libtool](http://ubuntuforums.org/showthread.php?t=945424&highlight=kdevelop+libtool)

---

