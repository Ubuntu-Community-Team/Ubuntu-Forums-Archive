---
title: "Installation of otcl/tclcl for network simulator 2"
date: 2008-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by ric_da_inf on 2008-05-22
Hello everybody!

I've an ubuntu hardy heron clear installed. I wanted to download and install the package network simulator 2 (ns-2) and all the package required "tcl/tk".

I run sudo apt-get install  tk8.4-dev tcl8.4-dev and then I download from site [http://www.isi.edu/nsnam/ns/ns-build.html](http://www.isi.edu/nsnam/ns/ns-build.html) the version 1.13 of otcl library for tcl.

When I try to run "./configure", I encountered a problem who stop the makefile creation process as :

--------------------------------------------
$ ./configure
No .configure file found in current directory
Continuing with default options...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
checking for string.h... (cached) yes
checking for main in -lXbsd... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for dcgettext in -lintl... no
checking for getnodebyname in -ldnet_stub... no
checking that g++ can handle -O2... no
checking standard STL is available... no
checking for tcl.h... -I/usr/include/tcl8.4/tcl-private/generic
checking for tclInt.h... -I/usr/include/tcl8.4/tcl-private/generic
checking for libtcl8.4... -L/usr/lib -ltcl8.4
checking for init.tcl... no
checking for http.tcl... no
checking Tcl http.tcl library... configure: error: Couldn't find http.tcl in  	 	/http 	/http2.4 	/http2.3 /http2.1 	/http2.0 	/http1.0 	
--------------------------------------------

The problem is in "configure" script, it seems there were wrong path to "init.tcl" and "http.tcl", you have to mod it adding :

- to variable
 TCL_TCL_PLACES="../lib/tcl$TCL_HI_VERS \
                ../lib/tcl$TCL_ALT_VERS \
                ../lib/tcl$TCL_VERS \
                ../lib/tcl \
                --------THIS NEW SEARCH PATH-----------
                /usr/share/tcltk/tcl$TCL_VERS \
                /usr/share/tcltk/tcl$TCL_HI_VERS \
                /usr/share/tcltk/tcl$TCL_ALT_VERS \
                --------THIS NEW SEARCH PATH-----------
                   ..............................

- to variable
TK_TCL_PLACES=" \
                ../lib/tk$TK_HI_VERS \
                ../lib/tk$TK_VERS \
                ../lib/tk$TK_ALT_VERS \
                ../tk$TK_VERS/library \
                ../tk$TK_ALT_VERS/library \
                ../tk$TK_HI_VERS/library \
                ../tk/library \
                --------THIS NEW SEARCH PATH-----------
                /usr/share/tcltk/tk$TK_VERS \
                /usr/share/tcltk/tk$TK_ALT_VERS \
                /usr/share/tcltk/tk$TK_HI_VERS \
                /usr/share/tcltk/tk$TK_VERS \
                --------THIS NEW SEARCH PATH-----------
                 ................


I hope this is usefull hint..

Long life and prosper

---

### Post by Fole on 2008-07-04
Try the following:
```

sudo ln -s /usr/share/tcltk/tcl8.4 /usr/share/
sudo ln -s /usr/share/tcltk/tk8.4 /usr/share/

```
Afterwards try ./configure again and it should also work fine without editing the config script.
Cheers, Florian

---

### Post by dummies85 on 2008-08-06
some extra tips i found 

[html]http://portal.chrost.com/gibbering/2-devel/11-installing-and-running-ns-2-on-ubuntu-710.html[/html]i used that guide for installation on 8.04, also i used

[html]http://nsnam.isi.edu/nsnam/index.php/Troubleshooting[/html]for some error i found
i hope this helps:)

---

### Post by manojpanguluru on 2008-09-16
hi,me too trying to install ns2 simulator. ths nsallinone package gives me an error during the otcl installation part. so i tried to install each one separately. i installed tcl 8.4.18 and tk8.4.18 successfully. but while installing otcl 1.13 i get the following error message

No .configure file found in current directory
Continuing with default options...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
checking for string.h... (cached) yes
checking for main in -lXbsd... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for dcgettext in -lintl... no
checking for getnodebyname in -ldnet_stub... no
checking that g++ can handle -O2... no
checking standard STL is available... no
checking for tcl.h... -I/usr/include
checking for tclInt.h... -I/usr/include
checking for libtcl8.4... -L/usr/lib -ltcl8.4
checking for init.tcl... /usr/lib/tcl8.4
checking for http.tcl... /usr/lib/tcl8.4/http1.0
checking Tcl http.tcl library... yes
checking for tclsh8.4.14... no
checking for tclsh8.4... /usr/bin/tclsh8.4
checking for tk.h... -I/usr/include
checking for libtk8.4... -L/usr/lib -ltk8.4
checking for tk.tcl... /usr/lib/tk8.4
checking for X11 header files
can't find X includes


can anyone help me on this please ?????

---

### Post by Nepherte on 2008-09-16
This ppa has ns2 (and nam): 
```
deb http://ppa.launchpad.net/wouterh/ubuntu hardy main
deb-src http://ppa.launchpad.net/wouterh/ubuntu hardy main
```

Just add it to /etc/apt/sources.list and run:
```
sudo apt-get update && sudo apt-get install ns nam
```

Link to the site:[http://wouter.horre.be/node/76](http://wouter.horre.be/node/76)

---

### Post by monder on 2009-02-16
Hi There,

I have to admit, i have been trying all Linux distros under the sun and by far the best is Ubuntu. life is simple after all. what made my day was being able to install ns2 using apt-get hassle free after installing it on RHL and Centos to no avail.

my only question is, can i install older version of ns2 using this method? in particular 2.26 and 2.1b9a. i am trying to run MPLS and ATM simulations and both run on older version of NS2.

Regards,
Munder

---

### Post by djgangstarr on 2010-08-01
Hello! ive been trying to install ns2.29 using the all in one package, it worked well with ubuntu 8 but now in ubuntu 10, there is a problem in the make part of otcl.

Please help!

---

