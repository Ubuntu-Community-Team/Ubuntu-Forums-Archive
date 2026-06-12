---
title: "Howto:  Install Giver (File share on Linux)"
date: 2007-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-07-06
[SIZE="3"]I would like to thank **[Puller]("http://thelinuxmovement.blogspot.com/2007/07/install-giver-easy-file-sharing-on.html")** for the information on how to install Giver.  Here is a cool video on how the program works:  [B][Giver Video]("http://thelinuxmovement.blogspot.com/2007/07/giver-easy-file-sharing-review.html")
[/B][/SIZE]

Install needed packages:
```
$ sudo apt-get install build-essential mercurial libmono-cairo2.0-cil mono mono-devel libmono-dev mono-gmcs monodoc
```

I don't have fiesty-backports turned on so I manually downloaded [B]avahi-sharp
[/B]
**Package site:**  [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=avahi-sharp](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=avahi-sharp)
**Download package here:**  [http://archive.ubuntu.com/ubuntu/pool/universe/a/avahi-sharp/](http://archive.ubuntu.com/ubuntu/pool/universe/a/avahi-sharp/)

```
$ wget [http://archive.ubuntu.com/ubuntu/pool/universe/a/avahi-sharp/libavahi1.0-cil_0.6.11-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/avahi-sharp/libavahi1.0-cil_0.6.11-1_all.deb)
```

```
$ dpkg -i libavahi1.0-cil_0.6.11-1_all.deb 
```

more software needed:
```
$ hg clone http://hg.circular-chaos.org/notify-sharp
```

```
$ cd notify-sharp/
```

```
$ autoscan
```

```
$ automake --add-missing
```

```
$ autoreconf
```

```
$ ./configure
```

```
$ make
```

```
$ sudo make install
```

```
$ cd ..
```

Now lets install Giver:

**Download Giver here:  **[http://code.google.com/p/giver/downloads/list](http://code.google.com/p/giver/downloads/list)

```
$ wget http://giver.googlecode.com/files/giver-0.1.4.tar.gz
```

```
$ tar -zxvf giver-0.1.4.tar.gz
```

```
$ cd giver-0.1.4/
```

```
$ ./configure
```

```
$ make
```

```
$ sudo make install
```

[COLOR="Red"]Some might have problems launching the program.  Running this command will help fix some of the problems:[/COLOR]
```
$ export MONO_PATH=/usr/local/lib/mono/notify-sharp
```

Now launch the program:

**Alt + F2 **
Type: **giver**

---

### Post by frodon on 2007-07-09
hum, is that really easier that NFS which is in the repo and has tools for it available ?

---

### Post by handband2 on 2007-07-09
NFS is still easier but I think myself (and others) would like to check out other projects which are being developed.

---

### Post by puccaso on 2007-12-16
i am trying to install on hardy

i get this error..
```

mahir@puccaso-lp:~/.config/giver$ giver
[Debug]: PhotoService static constructor called
[Debug]: New GiverService was created
[Debug]: We have the port : 54214
[Debug]: About to create the Avahi client
[Debug]: Adding Avahi Service  _giver._tcp
[Debug]: Avahi Service  _giver._tcp is added
[Debug]: GiverService:OnEntryGroupStateChanged was called state: Registering
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at Egg.TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.realized_cb(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at Giver.Application.SetupTrayIcon()
   at Giver.Application.InitializeIdle()
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Giver.Application.StartMainLoop()
   at Giver.Application.Main(System.String[] args)
```

---

### Post by puccaso on 2007-12-16
also another question.
can you answer your own questino please?
could you demonstrate how nfs and the nfs tools maybe simpler then giver? i'd very much like to use the simplest tool.

---

### Post by Forseti on 2008-05-19
> **puccaso said:**
> i am trying to install on hardy

i get this error..
```

mahir@puccaso-lp:~/.config/giver$ giver
[Debug]: PhotoService static constructor called
[Debug]: New GiverService was created
[Debug]: We have the port : 54214
[Debug]: About to create the Avahi client
[Debug]: Adding Avahi Service  _giver._tcp
[Debug]: Avahi Service  _giver._tcp is added
[Debug]: GiverService:OnEntryGroupStateChanged was called state: Registering
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at Egg.TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.realized_cb(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at Giver.Application.SetupTrayIcon()
   at Giver.Application.InitializeIdle()
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Giver.Application.StartMainLoop()
   at Giver.Application.Main(System.String[] args)
```

Had the same problem. Solved it installing **libgtk2.0-dev** in Synaptic (couple of deps though).

---

### Post by FaN_OnLy1 on 2008-06-27
Sorry to bring up the olds , but i wasn't able to install giver , although its really interesting me... , after following everything you've said , when i try to install notify-sharp i just end up with this :

```
lewis-laptop notify-sharp # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/lewis/notify-sharp/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... yes
checking for gmcs... /usr/bin/gmcs
checking for gacutil... /usr/bin/gacutil
checking for MONODOC... yes
checking for monodocer... /usr/bin/monodocer
checking for mdassembler... /usr/bin/mdassembler
checking for GTK_SHARP... yes
checking for NDESK_DBUS... yes
checking for Mono.Posix.dll... found
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in

```

i tried doing a "apt-get build-dep notify-sharp" but it ends up telling me ;```
E: Impossible de trouver une source de paquet pour notify-sharp

``` wich means in english : Unable to find a source package for notify-sharp.

darn i'm lost , could really use some help from you guys, ps: using a fresh install of Linux Mint Elyssa, wich stays alot similar from ubuntu , this cannot be the problem as i tried this on ubuntu and got the same error at the end... 

Cheers.

---

### Post by CameronCalver on 2008-07-14
i cannot get this to run when i run giver i get
```
cameron@ubuntu:~$ giver
exec: 9: -a: not found
cameron@ubuntu:~$ 

```

---

### Post by hypn0t0ad on 2008-11-18
i get the same error as Cameron.

Apparently, however, Giver seems to come pre-installed with the next release of Linux Mint (Felicia). So maybe there's a chance to actually use the app - it also makes a lot more sense: If several people use Mint (which is based on Ubuntu, btw), you can share all kinds of data without **any** hassle.

Until then, I'd like to get an solution to the problem:
```
exec: 9: -a: not found
```

EDIT:
I just found a solution:
[http://code.google.com/p/giver/issues/detail?id=3](http://code.google.com/p/giver/issues/detail?id=3)

---

### Post by groggyboy on 2008-11-19
i had the same problem, with "exec: 9: -a: not found".  i edited the file "/usr/local/bin/giver" and changed line 9 from ```
exec -a "Giver" mono "Giver.exe" "@$"
``` to ```
exec mono "Giver.exe" "@$"
```

now giver works fine.

---

### Post by srt4play on 2008-11-20
I am having trouble compiling giver v0.1.8.  Configure finishes ok but this is the output from the end of make:

```

Making all in po
make[1]: Entering directory `/home/user/giver-0.1.8/po'
file=`echo fi | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file fi.po
/bin/sh: -o: not found
make[1]: *** [fi.gmo] Error 127
make[1]: Leaving directory `/home/user/giver-0.1.8/po'
make: *** [all-recursive] Error 1
```

---

### Post by SikEnCide on 2009-01-15
I am running Hardy and I am having problems with .\configure can someone please help me out.


```
 ~/giver-0.1.8> ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gmcs... no
configure: error: gmcs Not found

```

---

### Post by directhex on 2009-01-15
> **srt4play said:**
> I am having trouble compiling giver v0.1.8.  Configure finishes ok but this is the output from the end of make:

```

Making all in po
make[1]: Entering directory `/home/user/giver-0.1.8/po'
file=`echo fi | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file fi.po
/bin/sh: -o: not found
make[1]: *** [fi.gmo] Error 127
make[1]: Leaving directory `/home/user/giver-0.1.8/po'
make: *** [all-recursive] Error 1
```

gettext package, then reconfigure.

---

### Post by directhex on 2009-01-15
> **SikEnCide said:**
> I am running Hardy and I am having problems with .\configure can someone please help me out.


```
 ~/giver-0.1.8> ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gmcs... no
configure: error: gmcs Not found

```

mono-2.0-devel package, then reconfogure

---

### Post by SikEnCide on 2009-01-15
> **directhex said:**
> gettext package, then reconfigure.
^
get what package??




I installed mono-2.0-devel package

tried to reconfigure and it failed.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gmcs... no

```

---

### Post by directhex on 2009-01-15
> **SikEnCide said:**
> ^
get what package??




I installed mono-2.0-devel package

tried to reconfigure and it failed.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gmcs... no

```

Perhaps it needs patching or something then.

Why not just upgrade to Intrepid & install the giver package

---

### Post by SikEnCide on 2009-01-15
> **directhex said:**
> Perhaps it needs patching or something then.

Why not just upgrade to Intrepid & install the giver package


Because Intrepid still will not connect to my college's wireless network which uses wpa2 enterprise. Doesn't work with network manager or wicd

---

### Post by majdi on 2009-11-09
Is there an ubuntu package to install Giver for 8.04 or do we have to do a cli install?

---

### Post by directhex on 2009-11-09
> **majdi said:**
> Is there an ubuntu package to install Giver for 8.04 or do we have to do a cli install?

Giver was only packaged in 8.10

---

### Post by majdi on 2009-11-09
I tried installing giver on 8.04.3 but i got this following error when running ./configure

Can someone please give us the steps to check first if all the dependencies are correctly installed? This is turning out to be a very complicated install for a small app. 


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles...
no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by directhex on 2009-11-09
> **majdi said:**
> I tried installing giver on 8.04.3 but i got this following error when running ./configure

Can someone please give us the steps to check first if all the dependencies are correctly installed? This is turning out to be a very complicated install for a small app. 


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles...
no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

[build-essential](apt:build-essential) package

---

### Post by majdi on 2009-11-14
Hi directhex,

Can you please elaborate.

---

