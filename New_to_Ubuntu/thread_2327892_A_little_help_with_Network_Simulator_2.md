---
title: "A little help with Network Simulator 2"
date: 2016-06-15
forum: New to Ubuntu
---

### Post by TropicalWolf on 2016-06-15
I must do a simple project using NS2, but I'm pretty new to the Ubuntu world, so I'm having some problems. In the first place, I tried to install NS2 (allinone), but I kept getting some problems, so I decided to go with the 
```
apt-get install ns2
```
Now I can use it without problems, but then I tried to follow the [tutorial]("http://www.isi.edu/nsnam/ns/tutorial/") and I have some problems with the "VII. A new protocol for ns" section. In the last part it says that I have to change some files. I tried to search for the package location using
```
dpkg -L ns2
```
but I can't file the files I have to change. Then searching a bit I found [this thread]("http://ubuntuforums.org/showthread.php?t=2193716&page=2"), so I tried to do these things:
1) Download the source
```
sudo apt-get build-dep ns2
```
2) Edit the files and then try to compile it again
```
cd ns2-2.35~rc10+dfsg/
./configure --prefix=/usr/local
```
3)
```
make
```
My problem is that when I try to use 
```
./configure
```
I always get this error:
```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
No .configure file found in current directory
Continuing with default options...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking for main in -lXbsd... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for dcgettext in -lintl... no
checking for getnodebyname in -ldnet_stub... no
checking that g++ can handle -O2... no
checking if C++ libraries work without any namespace... no
checking if C++ libraries work with namespace std... yes
checking if STL works without any namespace... no
checking if STL works with namespace std... yes
checking should use STL... yes
checking for tcl.h... no
checking for tclInt.h... no
checking for libtcl8.5... no
checking for init.tcl... /usr/share/tcltk/tcl8.5
checking for http.tcl... /usr/share/tcltk/tcl8.5/http1.0
checking Tcl http.tcl library... yes
checking for tclsh8.5.11... no
checking for tclsh8.5... /usr/bin/tclsh8.5
[B]configure: error: Installation of tcl seems incomplete or can't be found automatically.
Please correct the problem by telling configure where tcl is
using the argument --with-tcl=/path/to/package
(perhaps after installing it),
or the package is not required, disable it with --with-tcl=no.[/B]

```
As I already said, I'm new to this environment, so this may be a stupid thing, but I'd really like to get some help. Which directory does it want (/home/user/ns2-2.35~rc10+dfsg/tcl)? If I try with that directory, I get:
> ...
...
...
**checking Tcl http.tcl library... configure: error: Couldn't find http.tcl in       /http     /http2.5     /http2.4     /http2.3     /http2.1     /http2.0     /http1.0**     

What happens if I add?
```
**--with-tcl=no**
```
Thank you.

---

### Post by wildmanne39 on 2016-06-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

