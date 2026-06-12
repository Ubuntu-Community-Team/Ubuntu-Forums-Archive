---
title: "using ns-2 and omnetpp"
date: 2006-12-15
forum: Programming Talk
---

### Post by newsman on 2006-12-15
Has anyone any experience of installing ns-2 (discrete event simulator)


and omnetpp

any setup tipps


i managed to install omnetpp but i can't get the output right.

yesterday i was having issues with installing ns2 now i can apparently install it but its not the output they ([http://nsnam.isi.edu/nsnam/index.php/Downloading_and_installing_ns-2](http://nsnam.isi.edu/nsnam/index.php/Downloading_and_installing_ns-2)) say i should have,, instead i got this (and the subsequent validate script result in


============================================================
* Testing for Cygwin environment
============================================================
Cygwin not detected, proceeding with regular install.
============================================================
* Build XGraph-12.1
============================================================
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking if malloc debugging is wanted... no
checking for gcc... (cached) gcc-4.0
checking whether the C compiler (gcc-4.0  ) works... yes
checking whether the C compiler (gcc-4.0  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc-4.0 accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc-4.0 -E
checking for X... (cached) no
checking for float.h... (cached) yes
checking for limits.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking for strcasecmp... (cached) yes
creating ./config.status
creating Makefile
creating autoconf.h
autoconf.h is unchanged
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c xgraph.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c xgX.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c hard_devices.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c dialog.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c hpgl.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c ps.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c idraw.c
idraw.c: In function ‘idrawText’:
idraw.c:303: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c xtb.c
xtb.c: In function ‘focus_evt’:
xtb.c:873: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c:882: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c: In function ‘xtb_hort’:
xtb.c:1279: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c: In function ‘xtb_vert’:
xtb.c:1321: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c: In function ‘xtb_fmt_setpos’:
xtb.c:1351: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c: In function ‘xtb_fmt_addpos’:
xtb.c:1379: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c: In function ‘xtb_fmt_top’:
xtb.c:1520: warning: incompatible implicit declaration of built-in function ‘printf’
xtb.c:1529: warning: incompatible implicit declaration of built-in function ‘printf’
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c st.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c params.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c alloc.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c draw.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c init.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c read.c
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c tgif.c
tgif.c: In function ‘tgifText’:
tgif.c:230: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.        -g    -c derivative.c
gcc-4.0     -g     -o xgraph  xgraph.o xgX.o hard_devices.o dialog.o hpgl.o ps.o idraw.o xtb.o st.o params.o alloc.o draw.o init.o read.o tgif.o derivative.o     -lX11 -lm
xgraph has been installed successfully.
============================================================
* Build CWeb
============================================================
Making cweb
gcc -g   -c -o ctangle.o ctangle.c
ctangle.w:75: warning: conflicting types for built-in function ‘strlen’
gcc -g -DCWEBINPUTS=\"/usr/local/lib/cweb\" -c common.c
common.w:1409: warning: conflicting types for built-in function ‘strlen’
gcc -g -o ctangle ctangle.o common.o
gcc -g   -c -o cweave.o cweave.c
cweave.w:79: warning: conflicting types for built-in function ‘strlen’
gcc -g -o cweave cweave.o common.o
ln: creating symbolic link `cweave' to `/home/umar/ns-allinone-2.30/cweb/cweave': File exists
ln: creating symbolic link `ctangle' to `/home/umar/ns-allinone-2.30/cweb/ctangle': File exists
============================================================
* Build Stanford GraphBase
============================================================
Making sgb
gcc-4.0 -g -I/usr/local/sgb/include  test_io.c gb_io.o -o test_io
gcc-4.0 -g -I/usr/local/sgb/include  test_graph.c gb_graph.o -o test_graph
gcc-4.0 -g -I/usr/local/sgb/include  test_flip.c gb_flip.o -o test_flip
./test_io
OK, the gb_io routines seem to work!
./test_graph
....................................................................................................Hey, I allocated 10000000 bytes successfully. Terrific...
OK, the gb_graph routines seem to work!
./test_flip
OK, the gb_flip routines seem to work!
make gb_sort.o
make[1]: Entering directory `/home/umar/ns-allinone-2.30/sgb'
make[1]: `gb_sort.o' is up to date.
make[1]: Leaving directory `/home/umar/ns-allinone-2.30/sgb'
make lib
make[1]: Entering directory `/home/umar/ns-allinone-2.30/sgb'
make[1]: Nothing to be done for `lib'.
make[1]: Leaving directory `/home/umar/ns-allinone-2.30/sgb'
make test_sample
make[1]: Entering directory `/home/umar/ns-allinone-2.30/sgb'
gcc-4.0 -g -I/usr/local/sgb/include   -L. -L/usr/local/lib  test_sample.c -lgb -lgb -o test_sample
make[1]: Leaving directory `/home/umar/ns-allinone-2.30/sgb'
./test_sample > sample.out
diff test.gb test.correct
diff sample.out sample.correct
rm -f test.gb sample.out test_io test_io.exe test_graph test_graph.exe test_flip test_flip.exe test_sample test_sample.exe
echo "Congratulations --- the tests have all been passed."
Congratulations --- the tests have all been passed.
touch certified
============================================================
* Build GT-ITM
============================================================

and the subsequent ./validate script also results in everything not found..

i think because its ns-2.3 a newer version they might have premauturely finished the install script...


it should have finished according to website with following instructions:

Please put /home/myusername/ns-allinone-2.29/bin:/home/myusername/ns-allinone-2.29/tcl8.4.11/unix:/home/myusername/ns-allinone-2.29/tk8.4.11/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.

IMPORTANT NOTICES:

(1) You MUST put /home/myusername/ns-allinone-2.29/otcl-1.11, /home/myusername/ns-allinone-2.29/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
                setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
                export LD_LIBRARY_PATH=<paths>

(2) You MUST put /home/myusername/ns-allinone-2.29/tcl8.4.11/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.

(3) [OPTIONAL] To save disk space, you can now delete directories tcl8.4.11 
    and tk8.4.11. They are now installed under /home/myusername/ns-allinone-2.29/{bin,include,lib}

this might be causeing ./validate script to result in not found for all tests...how do i put this in my bash file?

---

### Post by newsman on 2006-12-15
if anyone knows of a deb repository for ns for ubuntu let me know cos i think it might be breaking my install for tk8.4-dev i am not sure actually, because the download instructions seam outdated (at least it appears to work but i din't get what they said i would get at the end of the script, anyhoo..) but in any case a deb package might be better so the directories are not all on my home directory..

---

### Post by Carlos Santiago on 2006-12-15
I followed the instructions and I install ns-2 with no problem.
However I also have a question. 
Do you know a ggod editor to work with ns-2? Preferable with GUI?
I would like it to have code completion and syntax highlight for both C++ and TCL.
Thanx

---

### Post by newsman on 2006-12-15
doesn't ns-2 all in one package also install nam,, i thought that was it,, i have yet to get started on working with it,, after i install it, however i came across that problem to use omnet and general c programming i need to do... at the moment i am using leafpad because it appears to be a extremely light program for editing (well slightly better than nano which was my previous favourite),, but no syntax highlighting in either.............. 

there is programmers notepad which only works in windows.. i was looking at tkpad, turbopad, and edt txt editor (all in sourceforge)..... 


it was so disappointing to see most notepad like apps i found in sourceforge were only for windows os.....

and of the above three, i have not tried any,,, and only turbopad mentions syntax highlighting....

if you do try them, let me know.... (my priority at the moment is installation still and getting basic programms working)

---

### Post by shooh on 2007-01-08
so any ns2 deb repository for ubuntu being released yet?

---

### Post by nanxy on 2007-08-24
Hi, i read that you manage to install omnet++ in UBuntu, is it? could you teach me how? i mean the steps or any website that i can refer to. i need to install it badly for my project...please....

---

### Post by newsman on 2008-01-20
I just managed to install ns-2 using these instructions on kubunutu hardy release


[http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04]("http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04")


For omnetpp please see.[http://www.omnetpp.org/pmwiki/index.php?n=Main.InstallingOnUnix]("http://www.omnetpp.org/pmwiki/index.php?n=Main.InstallingOnUnix")

Post any additions, etc.
:popcorn:

---

### Post by arejae on 2008-05-30
Hi everyone, I manage to install Omnet in Hardy Heron.

Here are the details.
[http://www.arejae.com/blog/how-to-install-omnet-in-ubuntu-804.html](http://www.arejae.com/blog/how-to-install-omnet-in-ubuntu-804.html)

Hope it helps. :)

---

