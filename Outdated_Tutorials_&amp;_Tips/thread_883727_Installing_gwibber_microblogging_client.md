---
title: "Installing gwibber microblogging client"
date: 2008-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2008-08-08
This is a guide to install the [gwibber]("https://edge.launchpad.net/gwibber") micro-blogging client on Ubuntu 8.04.

1. Install bazaar and subversion to download app and some needed libraries.
```
sudo apt-get install bzr subversion
```
2. Add the following ppa for webkit to apt sources.list or via **System -> Administration -> Software Sources**.
```
deb http://ppa.launchpad.net/stemp/ubuntu hardy main
```
3. Install webkit and development libraries
```
sudo apt-get install libwebkit-1.0-1 libwebkit-dev
```
4. Download pywebkitgtk
```
svn checkout http://pywebkitgtk.googlecode.com/svn/trunk/ pywebkitgtk-read-only
```
5. Install needed libraries and programs to compile pywebkitgtk.
```
sudo apt-get install build-essential autoconf libtool libgtk2.0-dev python-dev python-gtk2 python-gtk2-dev libsexy2 libsexy-dev python-sexy libxslt1-dev 
```
6. Goto pywebkitgtk-read-only directory - Configure, compile and install pywebkitgtk.
```
$ ./autogen.sh --prefix=/usr
$ make
$ sudo make install
```
7. Install need libraries and programs for gwibber
```
sudo apt-get install python-cairo-dev python-simplejson

```
8. Download gwibber webkitui
```
bzr branch lp:~segphault/gwibber/webkitui
```
9. Goto /webkitui directory to run gwibber
```
./run
```
10. or install
```
sudo python setup.py install
```

Improve this how-to at [https://wiki.ubuntu.com/gwibber]("https://wiki.ubuntu.com/gwibber")

Follow me on Twitter ([Technoviking]("http://twitter.com/Technoviking")) or better yet the open source identi.ca ([technoviking]("http://identi.ca/technoviking"))

---

### Post by quannum on 2008-09-16
> **Mike said:**
> 
6. Goto pywebkitgtk-read-only directory - Configure, compile and install pywebkitgtk.
```
$ ./autogen.sh --prefix=/usr
$ make
$ sudo make install
```


I see this when i execute make in pywebkitgtk-read-only

```

blah:~/workspace/pywebkitgtk-read-only$ make
make  all-am
make[1]: Entering directory `~/workspace/pywebkitgtk-read-only'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I/usr/include/python2.5   -I/usr/local/include/webkit-1.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -g -O2 -MT webkit_la-webkit.lo -MD -MP -MF .deps/webkit_la-webkit.Tpo -c -o webkit_la-webkit.lo `test -f 'webkit.c' || echo './'`webkit.c
 gcc -DHAVE_CONFIG_H -I. -I/usr/include/python2.5 -I/usr/local/include/webkit-1.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT webkit_la-webkit.lo -MD -MP -MF .deps/webkit_la-webkit.Tpo -c webkit.c  -fPIC -DPIC -o .libs/webkit_la-webkit.o
webkit.c: In function ‘pywebkit_add_constants’:
webkit.c:1638: error: ‘WEBKIT_TYPE_NAVIGATION_RESPONSE’ undeclared (first use in this function)
webkit.c:1638: error: (Each undeclared identifier is reported only once
webkit.c:1638: error: for each function it appears in.)
webkit.c:1639: error: ‘WEBKIT_TYPE_WEB_VIEW_TARGET_INFO’ undeclared (first use in this function)
make[1]: *** [webkit_la-webkit.lo] Error 1
make[1]: Leaving directory `~/workspace/pywebkitgtk-read-only'
make: *** [all] Error 2

```

I can only assume it's due to a change in the webkit library. Has anyone else managed to work around this error?

I'm using 8.04 with the latest updates.

---

### Post by quannum on 2008-09-16
> **quannum said:**
> I see this when i execute make in pywebkitgtk-read-only

```

blah:~/workspace/pywebkitgtk-read-only$ make
make  all-am
make[1]: Entering directory `~/workspace/pywebkitgtk-read-only'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -I/usr/include/python2.5   -I/usr/local/include/webkit-1.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -g -O2 -MT webkit_la-webkit.lo -MD -MP -MF .deps/webkit_la-webkit.Tpo -c -o webkit_la-webkit.lo `test -f 'webkit.c' || echo './'`webkit.c
 gcc -DHAVE_CONFIG_H -I. -I/usr/include/python2.5 -I/usr/local/include/webkit-1.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT webkit_la-webkit.lo -MD -MP -MF .deps/webkit_la-webkit.Tpo -c webkit.c  -fPIC -DPIC -o .libs/webkit_la-webkit.o
webkit.c: In function ‘pywebkit_add_constants’:
webkit.c:1638: error: ‘WEBKIT_TYPE_NAVIGATION_RESPONSE’ undeclared (first use in this function)
webkit.c:1638: error: (Each undeclared identifier is reported only once
webkit.c:1638: error: for each function it appears in.)
webkit.c:1639: error: ‘WEBKIT_TYPE_WEB_VIEW_TARGET_INFO’ undeclared (first use in this function)
make[1]: *** [webkit_la-webkit.lo] Error 1
make[1]: Leaving directory `~/workspace/pywebkitgtk-read-only'
make: *** [all] Error 2

```

I can only assume it's due to a change in the webkit library. Has anyone else managed to work around this error?

I'm using 8.04 with the latest updates.

I worked around this error by using pywebkitgtk-1.0.1.tar.gz instead, however I've got one final error:

```

blah:~$ gwibber 
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 11, in <module>
    from gwibber.client import GwibberClient
  File "/usr/lib/python2.5/site-packages/gwibber/client.py", line 10, in <module>
    import gtk, gtk.glade, gobject, table, webkit
ImportError: /usr/local/lib/libwebkit-1.0.so.1: undefined symbol: UCNV_FROM_U_CALLBACK_ESCAPE_3_6

```

---

### Post by gamgee911 on 2008-10-14
I'm getting the same error as quannum, I'm running 8.10 with latest updates.  please help :(

```
samuelgrund@samuelgrund-laptop:~/pywebkitgtk-read-only$ ./autogen.sh --prefix=/usr
libtoolize: putting auxiliary files in `.'.
libtoolize: linking file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: linking file `m4/libtool.m4'
libtoolize: linking file `m4/ltoptions.m4'
libtoolize: linking file `m4/ltsugar.m4'
libtoolize: linking file `m4/ltversion.m4'
libtoolize: linking file `m4/lt~obsolete.m4'
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:39: installing `./config.guess'
configure.ac:39: installing `./config.sub'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pywebkitgtk-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
./config.status: line 1118: ./stamp-h1: Permission denied
config.status: executing depfiles commands
config.status: executing libtool commands
samuelgrund@samuelgrund-laptop:~/pywebkitgtk-read-only$ make
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-am
make[1]: Entering directory `/home/samuelgrund/pywebkitgtk-read-only'
(cd . \
	 && /usr/bin/pygtk-codegen-2.0 \
	    --register /usr/share/pygtk/2.0/defs/gdk-types.defs \
	    --register /usr/share/pygtk/2.0/defs/gtk-types.defs \
	    --override webkit.override \
	    --prefix pywebkit webkit.defs) 2>&1 >gen-webkit.c | tee webkit.errors \
	&& ! grep -q -v "^\*\*\*INFO\*\*\*" webkit.errors \
	&& cp gen-webkit.c webkit.c \
	&& rm -f gen-webkit.c
note: pygtk-codegen-2.0 is deprecated, use pygobject-codegen-2.0 instead
note: I will now try to invoke pygobject-codegen-2.0 in the same directory
***INFO*** There are no declared global functions.
***INFO*** The coverage of methods is 100.00% (73/73)
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
make[1]: *** [webkit.c] Error 1
make[1]: Leaving directory `/home/samuelgrund/pywebkitgtk-read-only'
make: *** [all] Error 2

```

---

### Post by quannum on 2008-10-14
> **gamgee911 said:**
> I'm getting the same error as quannum, I'm running 8.10 with latest updates.  please help :(

```
samuelgrund@samuelgrund-laptop:~/pywebkitgtk-read-only$ ./autogen.sh --prefix=/usr
libtoolize: putting auxiliary files in `.'.
libtoolize: linking file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: linking file `m4/libtool.m4'
libtoolize: linking file `m4/ltoptions.m4'
libtoolize: linking file `m4/ltsugar.m4'
libtoolize: linking file `m4/ltversion.m4'
libtoolize: linking file `m4/lt~obsolete.m4'
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:39: installing `./config.guess'
configure.ac:39: installing `./config.sub'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pywebkitgtk-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
./config.status: line 1118: ./stamp-h1: Permission denied
config.status: executing depfiles commands
config.status: executing libtool commands
samuelgrund@samuelgrund-laptop:~/pywebkitgtk-read-only$ make
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-am
make[1]: Entering directory `/home/samuelgrund/pywebkitgtk-read-only'
(cd . \
	 && /usr/bin/pygtk-codegen-2.0 \
	    --register /usr/share/pygtk/2.0/defs/gdk-types.defs \
	    --register /usr/share/pygtk/2.0/defs/gtk-types.defs \
	    --override webkit.override \
	    --prefix pywebkit webkit.defs) 2>&1 >gen-webkit.c | tee webkit.errors \
	&& ! grep -q -v "^\*\*\*INFO\*\*\*" webkit.errors \
	&& cp gen-webkit.c webkit.c \
	&& rm -f gen-webkit.c
note: pygtk-codegen-2.0 is deprecated, use pygobject-codegen-2.0 instead
note: I will now try to invoke pygobject-codegen-2.0 in the same directory
***INFO*** There are no declared global functions.
***INFO*** The coverage of methods is 100.00% (73/73)
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
make[1]: *** [webkit.c] Error 1
make[1]: Leaving directory `/home/samuelgrund/pywebkitgtk-read-only'
make: *** [all] Error 2

```

Try using the tarball[0] instead of the svn version.

[0] [http://code.google.com/p/pywebkitgtk/downloads/detail?name=pywebkitgtk-1.0.1.tar.gz&can=2&q=](http://code.google.com/p/pywebkitgtk/downloads/detail?name=pywebkitgtk-1.0.1.tar.gz&can=2&q=)

---

### Post by ExpatPaul on 2008-11-05
> **quannum said:**
> I worked around this error by using pywebkitgtk-1.0.1.tar.gz instead, however I've got one final error:

```

blah:~$ gwibber 
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 11, in <module>
    from gwibber.client import GwibberClient
  File "/usr/lib/python2.5/site-packages/gwibber/client.py", line 10, in <module>
    import gtk, gtk.glade, gobject, table, webkit
ImportError: /usr/local/lib/libwebkit-1.0.so.1: undefined symbol: UCNV_FROM_U_CALLBACK_ESCAPE_3_6

```

I hit the same problem. You can fix it by installing the pywebkitgtk deb from here: [https://code.launchpad.net/~jorge/+archive](https://code.launchpad.net/~jorge/+archive)

---

### Post by quannum on 2008-11-05
> **ExpatPaul said:**
> I hit the same problem. You can fix it by installing the pywebkitgtk deb from here: [https://code.launchpad.net/~jorge/+archive](https://code.launchpad.net/~jorge/+archive)

I already had that package installed :(

I did, however, finally fix it by removing the shared objects i.e.

  rm -rf /usr/local/lib/libwebkit-1.0.*
  ldconfig

I can only assume that the version I had installed from source had precedence over the packaged version.

Isn't gwibber great?!

---

### Post by ExpatPaul on 2008-11-06
> **quannum said:**
> Isn't gwibber great?!

It's very nice indeed. But does have the potential to be dangerously addictive.

---

### Post by steevc on 2008-12-19
I tried the install from source on the wiki, but when I run gwibber I get 

```

Traceback (most recent call last):
  File "./run", line 18, in <module>
    from gwibber.client import GwibberClient
  File "/home/steve/bzr/gwibber/gwibber/client.py", line 10, in <module>
    import gtk, gtk.glade, gobject, table, webkit, simplejson
ImportError: No module named webkit
```

So I assume that something is not quite right. I didn't notice any error messages along the way.

Is there any possibility that gwibber will get easier to install? I can see a lot of people being turned off by a page of instructions like that.

---

### Post by ExpatPaul on 2008-12-20
> **steevc said:**
> Is there any possibility that gwibber will get easier to install?

Yes. You need to edit your repositories in Synaptic ([instructions here]("https://wiki.ubuntu.com/gwibber")) and then it is a very straightforward process.

---

### Post by steevc on 2008-12-21
> **ExpatPaul said:**
> Yes. You need to edit your repositories in Synaptic ([instructions here]("https://wiki.ubuntu.com/gwibber")) and then it is a very straightforward process.

I created a gwibber.list file with those two PPAs, but cannot see python-webkitgtk python-egenix-mxdatetime and gwibber in Adept. I'm still on 8.04.

---

### Post by ExpatPaul on 2008-12-22
> **steevc said:**
> I created a gwibber.list file with those two PPAs, but cannot see python-webkitgtk python-egenix-mxdatetime and gwibber in Adept. I'm still on 8.04.

Okay, I'm also on 8.04 and the following worked for me and may be worth trying...

Open Synaptic and go to Settings>Repositories
In the Third Party Software Tab, add the four APT lines 
[INDENT]deb [http://ppa.launchpad.net/gwibber-team/ubuntu](http://ppa.launchpad.net/gwibber-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gwibber-team/ubuntu](http://ppa.launchpad.net/gwibber-team/ubuntu) hardy main
deb [http://ppa.launchpad.net/webkit-team/ubuntu](http://ppa.launchpad.net/webkit-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/webkit-team/ubuntu](http://ppa.launchpad.net/webkit-team/ubuntu) hardy main[/INDENT]
Close the dialogue and click the Reload button
You should now be able to search for Gwibber in Synaptic and then simply right click on it to mark for install and apply

Good luck.

---

### Post by steevc on 2008-12-24
@ExPatPaul I just tried that again and it worked, so not sure why it didn't before.

So now I have Gwibber installed and my Twitter/Identi.ca accounts set up (both steevc), but I don't see any messages in the window. I do get bubbles when new stuff comes in. I see someone posted the same issue to Launchpad.

Apart from that it looks like it has most of the features I want. If I can get past this initial hurdle then I will be happy to provide feedback.

EDIT: I see this has been logged as a bug related to Webkit. I installed the older version and now it works :)

[https://bugs.launchpad.net/gwibber/+bug/304033](https://bugs.launchpad.net/gwibber/+bug/304033)

---

### Post by dimeotane on 2008-12-31
I'm on hardy and have the same problem:  message pop up, but nothing appears in the gwibber window itself.  I followed the install method listed on [https://wiki.ubuntu.com/gwibber](https://wiki.ubuntu.com/gwibber)
 from repository. 

I also tried the other gwibber installation methods posted online for hardy and all gave errors.


SOLUTION:
Ok, after a few hours of questionable time spend fishing around to play trial and error this worked for me.  This installs an older version of libwebkit, and a 0.7.3 version of gwibber.

First remove the old files and repositories first then install these three DEBS:

[http://ppa.launchpad.net/stemp/ubuntu/pool/main/w/webkit/libwebkit-1.0-1_1.0.1-4+r38688~hardyppa2_i386.deb](http://ppa.launchpad.net/stemp/ubuntu/pool/main/w/webkit/libwebkit-1.0-1_1.0.1-4+r38688~hardyppa2_i386.deb)

[https://launchpad.net/%7Ejorge/+archive/+files/python-webkitgtk_1.0.2~hardy~ppa2_i386.deb](https://launchpad.net/%7Ejorge/+archive/+files/python-webkitgtk_1.0.2~hardy~ppa2_i386.deb)

[https://launchpad.net/%7Ejorge/+archive/+files/gwibber_0.7.3~bzr175~hardy~ppa1_i386.deb](https://launchpad.net/%7Ejorge/+archive/+files/gwibber_0.7.3~bzr175~hardy~ppa1_i386.deb)

---

### Post by niessuh on 2009-02-08
How about for intrepid (8.10) I still can't install. I have added the repositories but still can't see gwibber in synaptic.

---

