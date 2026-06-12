---
title: "FreeSWITCH/mod_managed: jit.h and glib.h Not Found"
date: 2010-07-16
forum: Packaging and Compiling Programs
---

### Post by GraysonPeddie on 2010-07-16
FreeSWITCH version: 1.0.6
Ubuntu Version: 10.10 Alpha 2 (I like to be in the "bleeding edge" while still using apt-get. :) Heh. But I digress.)
Mono Version: 20100618 (Tarball Fri Jul 16 10:03:48 EDT 2010)
I've compiled Mono from trunk.
FreeSWITCH installed path: /usr/local/freeswitch

Output of make in src/mod/languages/mod_managed:

```
grayson@server:~/src/freeswitch/src/mod/languages/mod_managed$ make
make[1]: Entering directory `/home/grayson/src/freeswitch/src/mod/languages/mod_
managed'
Compiling freeswitch_managed.cpp...
g++ -I/home/grayson/src/freeswitch/src/include -I/home/grayson/src/freeswitch/sr
c/include -I/home/grayson/src/freeswitch/libs/libteletone/src -fPIC -fvisibility
=hidden -DSWITCH_API_VISIBILITY=1 -DHAVE_VISIBILITY=1 -g -O2 -D_GNU_SOURCE -DHAV
E_CONFIG_H -c -o freeswitch_managed.o freeswitch_managed.cpp
In file included from freeswitch_managed.cpp:35:
freeswitch_managed.h:43:18: error: glib.h: No such file or directory
freeswitch_managed.h:44:26: error: mono/jit/jit.h: No such file or directory
freeswitch_managed.h:45:36: error: mono/metadata/assembly.h: No such file or dir
ectory
freeswitch_managed.h:46:39: error: mono/metadata/environment.h: No such file or
directory
freeswitch_managed.h:47:39: error: mono/metadata/mono-config.h: No such file or
directory
freeswitch_managed.h:48:35: error: mono/metadata/threads.h: No such file or dire
ctory
freeswitch_managed.h:49:41: error: mono/metadata/debug-helpers.h: No such file o
r directory
In file included from freeswitch_managed.cpp:35:
freeswitch_managed.h:56: error: ISO C++ forbids declaration of `MonoDomain' with
 no type
freeswitch_managed.h:56: error: expected `;' before `*' token
freeswitch_managed.h:57: error: ISO C++ forbids declaration of `MonoAssembly' wi
th no type
freeswitch_managed.h:57: error: expected `;' before `*' token
freeswitch_managed.h:60: error: ISO C++ forbids declaration of `MonoMethod' with
 no type
freeswitch_managed.h:60: error: expected `;' before `*' token
freeswitch_managed.cpp: In destructor `virtual ManagedSession::~ManagedSession()
':
freeswitch_managed.cpp:68: error: `struct mod_managed_globals' has no member nam
ed `domain'
freeswitch_managed.cpp:68: error: `mono_thread_attach' was not declared in this
scope
freeswitch_managed.cpp: In member function `virtual void ManagedSession::check_h
angup_hook()':
freeswitch_managed.cpp:83: error: `struct mod_managed_globals' has no member nam
ed `domain'
freeswitch_managed.cpp:83: error: `mono_thread_attach' was not declared in this
scope
freeswitch_managed.cpp: In member function `virtual switch_status_t ManagedSessi
on::run_dtmf_callback(void*, switch_input_type_t)':
freeswitch_managed.cpp:93: error: `struct mod_managed_globals' has no member nam
ed `domain'
freeswitch_managed.cpp:93: error: `mono_thread_attach' was not declared in this
scope
freeswitch_managed.cpp:101: error: `g_free' was not declared in this scope
make[1]: *** [freeswitch_managed.o] Error 1
make[1]: Leaving directory `/home/grayson/src/freeswitch/src/mod/languages/mod_m
anaged'
make: *** [all] Error 1
```

Locate jit.h:
/usr/local/include/mono-2.0/mono/jit/jit.h

Locate glib.h
/usr/local/glib-2.0/glib.h

I have those files. What can I do to solve this problem?

---

### Post by SevenMachines on 2010-07-16
do you need local builds of glib and mono too? if not, use the repository version, if you do, you'll need to add the manual build include paths to the makefile

---

### Post by GraysonPeddie on 2010-07-16
Okay, here's what I got:

```
LOCAL_INSERT_CFLAGS= /usr/bin/pkg-config mono --cflags
LOCAL_INSERT_LDFLAGS= /usr/bin/pkg-config mono --libs
#MOD_CFLAGS=-D_REENTRANT -pthread -I/usr/local/include/mono-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -lmono
BASE=../../../..
VERBOSE=1
include $(BASE)/build/modmake.rules
LOCAL_OBJS=freeswitch_managed.o freeswitch_wrap.o

local_depend: $(LOCAL_OBJS)

freeswitch_managed.o: freeswitch_managed.h freeswitch_managed.cpp

freeswitch_wrap.o: freeswitch_wrap.cpp

freeswitch_wrap.cpp: freeswitch_wrap.cxx
	cp freeswitch_wrap.cxx freeswitch_wrap.cpp

reswig: swigclean freeswitch_wrap.cxx

local_depend:
	cd managed && $(MAKE)

local_install: $(DESTDIR)$(modulesdir)/mod_managed.$(LIBTOOL_LIB_EXTEN)
	cd managed && $(MAKE) INSTALL="$(LTINSTALL)" MODINSTDIR=$(modulesdir) DESTDIR=$(DESTDIR) install

local_uninstall:
	rm -fr $(DESTDIR)$(modulesdir)/mod_managed.so
	cd managed && $(MAKE) UNINSTALL="$(LTUNINSTALL)" MODINSTDIR=$(modulesdir) uninstall

local_clean:
	cd managed && $(MAKE) clean

swigclean: clean
	rm -f freeswitch_wrap.cxx freeswitch_wrap.cpp managed/swig.cs

freeswitch_wrap.cxx:
	swig -I../../../include -v -O -c++ -csharp -namespace FreeSWITCH.Native -dllimport mod_managed -DSWIG_CSHARP_NO_STRING_HELPER freeswitch.i
	rm -f ./managed/swig.cs
	cat *.cs > ./managed/swig.cs
	rm -f *.cs

depend_install:
	mkdir -p $(DESTDIR)$(modulesdir)/managed

```

It still did not work, though.

I wanted to compile Mono 2.6. Ubuntu 10.04 has Mono 2.4 and I wanted 2.6 since I like to be in the cutting edge. I think GLib is already installed.

---

### Post by SevenMachines on 2010-07-16
generally you'd do something like
$ CPPFLAGS+="-I/path/to/strange/include/dir/" ./configure
and then make will run with that directory added

with something like glib, it has a lot of dependencies so you're probably right to use pkg-config, but, unless the .pc files are on the default path they wont be found. in that case you might want something like,
$CPPFLAGS+=`PKG_CONFIG_PATH=/odd/path/to/somelib.pc/dir/ pkg-config --cflags somelib` ./configure

---

### Post by GraysonPeddie on 2010-07-16
Hmm... Then I can't remember what I erased from the Makefile (should've done a backup). :(

Thanks.

PS: I am following instructions from here (Linux Build):
[http://wiki.freeswitch.org/wiki/Mod_managed](http://wiki.freeswitch.org/wiki/Mod_managed)

But there isn't a src/mod/mod_managed as this document seems to be out of date as I'm using FreeSWITCH 1.0.6. It's now src/mod/languages/mod_managed instead. As far as I've checked, there isn't a configure script inside the mod_managed folder.

Hmm... I'm gonna have to check to see if I could build FreeSWITCH with modules included when I execute a ./configure script.

---

### Post by SevenMachines on 2010-07-16
sorry, i hadnt actually looked at the freeswitch source and was being a bit generic, and a bit 'friday evening:)'. if you uncomment the MOD_CFLAGS line in the Makefile to something like

MOD_CFLAGS=-D_REENTRANT -pthread -I/usr/local/include/mono-2.0/ -I/usr/local/glib-2.0 -I/usr/lib/glib-2.0/include -lmono

you'll need to check the paths (glib especially seems to be in an odd arrangement) but you get the idea

[EDIT] if glib is really installed from the repositories and the Locate you mentioned above was a typo, ie
$locate glib.h
/usr/include/glib-2.0/glib.h

then try,
MOD_CFLAGS=-D_REENTRANT -pthread -I/usr/local/include/mono-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -lmono

---

### Post by GraysonPeddie on 2010-07-16
Ah... How did I miss that comment symbol (#)? Well, I got it.

Thanks for your help.

Update:

Okay, here's something that I got:

```
grayson@server:~/src/freeswitch/src/mod/languages/mod_managed$ make
make[1]: Entering directory `/home/grayson/src/freeswitch/src/mod/languages/mod_managed'
Compiling freeswitch_managed.cpp...
g++ -D_REENTRANT -pthread -I/usr/local/include/mono-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -lmono -I/home/grayson/src/freeswitch/src/include -I/home/grayson/src/freeswitch/src/include -I/home/grayson/src/freeswitch/libs/libteletone/src -fPIC -fvisibility=hidden -DSWITCH_API_VISIBILITY=1 -DHAVE_VISIBILITY=1 -g -O2 -D_GNU_SOURCE -DHAVE_CONFIG_H -c -o freeswitch_managed.o freeswitch_managed.cpp
cp freeswitch_wrap.cxx freeswitch_wrap.cpp
Compiling freeswitch_wrap.cpp...
g++ -D_REENTRANT -pthread -I/usr/local/include/mono-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -lmono -I/home/grayson/src/freeswitch/src/include -I/home/grayson/src/freeswitch/src/include -I/home/grayson/src/freeswitch/libs/libteletone/src -fPIC -fvisibility=hidden -DSWITCH_API_VISIBILITY=1 -DHAVE_VISIBILITY=1 -g -O2 -D_GNU_SOURCE -DHAVE_CONFIG_H -c -o freeswitch_wrap.o freeswitch_wrap.cpp
cd managed && make
make[2]: Entering directory `/home/grayson/src/freeswitch/src/mod/languages/mod_managed/managed'
gmcs -target:library -out:FreeSWITCH.Managed.dll AssemblyInfo.cs Extensions.cs Loader.cs Log.cs ManagedSession.cs PluginInterfaces.cs PluginManager.cs ScriptPluginManager.cs ChannelVariables.cs Util.cs swig.cs XmlSearchBinding.cs
XmlSearchBinding.cs(57,54): warning CS0414: The private field `FreeSWITCH.SwitchXmlSearchBinding.del' is assigned but its value is never used
Compilation succeeded - 1 warning(s)
make[2]: Leaving directory `/home/grayson/src/freeswitch/src/mod/languages/mod_managed/managed'
make[1]: *** No rule to make target `/home/grayson/src/freeswitch/libfreeswitch.la', needed by `mod_managed.la'.  Stop.
make[1]: Leaving directory `/home/grayson/src/freeswitch/src/mod/languages/mod_managed'
make: *** [all] Error 1
``` Heh! This is confusing for me.

```
grayson@server:~/src/freeswitch$ locate libfreeswitch.la
/usr/local/freeswitch/lib/libfreeswitch.la
```

---

### Post by SevenMachines on 2010-07-17
The build expects you to have 'make'd' all the freeswitch libraries in the base directory, where it would have left libfreeswitch.la. so you could either...

1. configure and make in the base directory to build all the source

2. if you look in {base_dir}/build/modmake.rules you'll see the line
LIBS=$(switch_builddir)/libfreeswitch.la
which you could change to 
LIBS=/usr/local/freeswitch/lib/libfreeswitch.la
then make mod_managed

3. link /usr/local/freeswitch/lib/libfreeswitch.la
to the source base directory then make mod_managed

options 2 & 3 are a bit 'hacky' but should work for playing around with the module, best to do option 1 if your not in a big hurry

---

### Post by GraysonPeddie on 2010-07-17
Okay, thanks for your help.

---

