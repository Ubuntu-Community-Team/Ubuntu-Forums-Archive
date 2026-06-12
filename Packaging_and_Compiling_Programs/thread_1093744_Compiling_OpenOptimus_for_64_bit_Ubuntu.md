---
title: "Compiling OpenOptimus for 64 bit Ubuntu"
date: 2009-03-11
forum: Packaging and Compiling Programs
---

### Post by Keith_Beef on 2009-03-11
I'm perplexed by the result I get when I try to compile OpenOptimus, downloaded from the SVN repository.


```
svn co http://ookoo.org/svn/openoptimus/ -r52
cd openoptimus/trunk/
make
make[1]: Entering directory `/home/klrhodes/OpenOptimus/openoptimus/trunk/src_liboptimususb'
gcc -ggdb -Wall -O0 --std=gnu99 -D__DEBUG -D_REENTRANT -I. -I"/home/klrhodes/OpenOptimus/openoptimus/trunk" -I"/home/klrhodes/OpenOptimus/openoptimus/trunk/src_liboptimususb" -D_LIBOPTIMUSUSB -D_HAVE_SOURCE_FOR_MINITHREE -D_HAVE_SOURCE_FOR_OLED_IMAGE -D_HAVE_SOURCE_FOR_USB_MAIN   -c -o minithree.o minithree.c
minithree.c:19:17: error: usb.h: No such file or directory
In file included from minithree.c:21:
optimususb.h:12: error: expected ‘)’ before ‘*’ token
optimususb.h:13: error: expected ‘;’ before ‘_Bool’
minithree.c:66: error: expected ‘)’ before ‘*’ token
minithree.c:101: error: expected ‘)’ before ‘*’ token
minithree.c:118: error: expected ‘)’ before ‘*’ token
minithree.c:146: error: expected ‘)’ before ‘*’ token
minithree.c:167: error: expected ‘)’ before ‘*’ token
minithree.c:176: error: expected ‘)’ before ‘*’ token
minithree.c:188: error: expected ‘)’ before ‘*’ token
minithree.c:222: error: expected ‘)’ before ‘*’ token
minithree.c:275: error: expected ‘)’ before ‘*’ token
minithree.c:281: error: expected ‘)’ before ‘*’ token
minithree.c:289: error: expected ‘)’ before ‘*’ token
minithree.c:297: error: expected ‘)’ before ‘*’ token
minithree.c:334: error: expected ‘)’ before ‘*’ token
minithree.c:345: error: ‘init_oled_minithree’ undeclared here (not in a function)
minithree.c:345: warning: excess elements in struct initializer
minithree.c:345: warning: (near initialization for ‘module_info’)
minithree.c:346: error: ‘shutdown_oled_minithree’ undeclared here (not in a function)
minithree.c:346: warning: excess elements in struct initializer
minithree.c:346: warning: (near initialization for ‘module_info’)
minithree.c:347: error: ‘do_usb_serial_oled_noop’ undeclared here (not in a function)
minithree.c:347: warning: excess elements in struct initializer
minithree.c:347: warning: (near initialization for ‘module_info’)
minithree.c:348: error: ‘usb_get_oled_event’ undeclared here (not in a function)
minithree.c:348: warning: excess elements in struct initializer
minithree.c:348: warning: (near initialization for ‘module_info’)
minithree.c:349: error: ‘do_usb_serial_set_brightness’ undeclared here (not in a function)
minithree.c:349: warning: excess elements in struct initializer
minithree.c:349: warning: (near initialization for ‘module_info’)
minithree.c:350: error: ‘minithree_load_image_file’ undeclared here (not in a function)
minithree.c:350: warning: excess elements in struct initializer
minithree.c:350: warning: (near initialization for ‘module_info’)
minithree.c:351: error: ‘do_usb_show_image’ undeclared here (not in a function)
minithree.c:352: warning: excess elements in struct initializer
minithree.c:352: warning: (near initialization for ‘module_info’)
make[1]: *** [minithree.o] Error 1
make[1]: Leaving directory `/home/klrhodes/OpenOptimus/openoptimus/trunk/src_liboptimususb'
make: *** [liboptimususb.a] Error 2
```

What's wrong with these lines?
Line 12 in optimususb.h is below.
```
bool (*init_func)(usb_dev_handle *);
```

Line 66 in minithree.c is below.
```
static bool do_usb_serial_oled_sync(usb_dev_handle *oled_udev) {
```

I don't see anything glaringly obvious...

Can anybody help me out?

Beef.

---

### Post by StrangeFreedom on 2009-05-11
the wiki isnt up to date. try r113. See [http://ookoo.org/svn/openoptimus/](http://ookoo.org/svn/openoptimus/)

---

### Post by Keith_Beef on 2012-04-01
It's been about a year since I tried compiling, and I found the OM3 sitting in a pile of cables and controllers a couple of days ago and decided to have another go at making this work...

I downloaded r113 from SVN, and tried to run the ./configure script.
```
sudo svn co http://ookoo.org/svn/openoptimus/ -r113
su chmod a+x openoptimus/trunk/optimusdaemon/configure.ac
sudo chmod a+x openoptimus/trunk/optimusdaemon/configure.ac
cd openoptimus/trunk/optimusdaemon/
sudo ./configure.ac 
./configure.ac: 1: Syntax error: word unexpected (expecting ")")
```

Hmm... is it because I'm running this as root?

Try it as a normal user, then.
```
./configure.ac 
./configure.ac: line 1: syntax error near unexpected token `2.62'
./configure.ac: line 1: `AC_PREREQ(2.62)'
```

Still not working...
I downloaded the code as root, maybe that's the problem... so change everything to belong to me and try again.
```
cd ../../..
sudo chown -R me:users ./openoptimus
cd openoptimus/trunk/optimusdaemon/
./configure.ac
./configure.ac: line 1: syntax error near unexpected token `2.62'
./configure.ac: line 1: `AC_PREREQ(2.62)'
```

Still the same problem.

Here are the first few lines of the configure.ac script.
```
AC_PREREQ(2.62)
AC_INIT([optimusdaemon], [0.1.1dev], [mark@hell.ne.jp])
AC_COPYRIGHT([Copyright (c) 2007 - 2009 Mark Karpeles <mark@hell.ne.jp>])
AM_INIT_AUTOMAKE
```

I've googled around for more info, but not found anything useful or up-to-date.

Has anybody managed to successfully compile and run this code?

---

### Post by SevenMachines on 2012-04-01
configure.ac isnt a script to run, its the input file for autoconf. also, sudo isnt necessary. try this instead
```
$ svn co http://ookoo.org/svn/openoptimus/ -r113
$ cd openoptimus/trunk/optimusdaemon/
$ ./buildconf 
$ ./configure
$ ./make
```
buildconf is just an included script to run autotools updates

---

### Post by Keith_Beef on 2012-04-01
> **SevenMachines said:**
> configure.ac isnt a script to run, its the input file for autoconf. also, sudo isnt necessary. try this instead
```
$ svn co http://ookoo.org/svn/openoptimus/ -r113
$ cd openoptimus/trunk/optimusdaemon/
$ ./buildconf 
$ ./configure
$ ./make
```
buildconf is just an included script to run autotools updates

Thanks for the info... I remember in the past using ./configure && make && make install for code from other projects, and the READMEs for OpenOptimus are not exactly helpful.

```
cd trunk/optimusdaemon/
./buildconf 
[: 10: unexpected operator
configure.ac:71: installing `./compile'
configure.ac:4: installing `./install-sh'
configure.ac:4: installing `./missing'
plugins/minithree/Makefile.am: installing `./depcomp'
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to build with debug information... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking for library containing strerror... none required
checking for a sed that does not truncate output... /bin/sed
checking for gawk... (cached) gawk
checking for ranlib... ranlib
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for int32_t... yes
checking for int64_t... yes
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint8_t... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether byte ordering is bigendian... no
checking for working volatile... yes
checking for inline... inline
checking for memmove... yes
checking for memset... yes
checking for strdup... yes
checking for library containing pow... -lm
checking for library containing floor... none required
checking for pow... yes
checking for floor... yes
checking for library containing socket... none required
checking for select... yes
checking for socket... yes
checking for usb_init in -lusb... yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for pthread_create in -lpthread... yes
checking whether to enable Optimus MiniThree support... yes
configure: creating ./config.status
config.status: creating plugins/minithree/Makefile
config.status: creating src/plugins_init.c
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating include/optimusdaemon/config.h
config.status: executing depfiles commands
make
Making all in plugins/minithree
make[1]: Entering directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../../include/optimusdaemon     -g -ggdb -O0 -I../../include -MT minithree.o -MD -MP -MF .deps/minithree.Tpo -c -o minithree.o minithree.c
mv -f .deps/minithree.Tpo .deps/minithree.Po
rm -f libminithree.a
ar cru libminithree.a minithree.o 
ranlib libminithree.a
make[1]: Leaving directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
Making all in src
make[1]: Entering directory `/usr/local/src/openoptimus/trunk/optimusdaemon/src'
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT cfg_files.o -MD -MP -MF .deps/cfg_files.Tpo -c -o cfg_files.o cfg_files.c
mv -f .deps/cfg_files.Tpo .deps/cfg_files.Po
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT network.o -MD -MP -MF .deps/network.Tpo -c -o network.o network.c
mv -f .deps/network.Tpo .deps/network.Po
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT optimus_image.o -MD -MP -MF .deps/optimus_image.Tpo -c -o optimus_image.o optimus_image.c
mv -f .deps/optimus_image.Tpo .deps/optimus_image.Po
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT usb_main.o -MD -MP -MF .deps/usb_main.Tpo -c -o usb_main.o usb_main.c
mv -f .deps/usb_main.Tpo .deps/usb_main.Po
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../include/optimusdaemon     -g -ggdb -O0 -I../include -MT plugins_init.o -MD -MP -MF .deps/plugins_init.Tpo -c -o plugins_init.o plugins_init.c
mv -f .deps/plugins_init.Tpo .deps/plugins_init.Po
gcc -std=gnu99  -g -ggdb -O0 -I../include   -o optimusdaemon main.o cfg_files.o network.o optimus_image.o usb_main.o plugins_init.o ../plugins/minithree/libminithree.a -lpthread -lusb -lm 
make[1]: Leaving directory `/usr/local/src/openoptimus/trunk/optimusdaemon/src'
make[1]: Entering directory `/usr/local/src/openoptimus/trunk/optimusdaemon'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/usr/local/src/openoptimus/trunk/optimusdaemon'
make install
Making install in plugins/minithree
make[1]: Entering directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
make[2]: Entering directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /usr/bin/install -c -m 644  libminithree.a '/usr/local/lib'
/usr/bin/install: cannot create regular file `/usr/local/lib/libminithree.a': Permission denied
make[2]: *** [install-libLIBRARIES] Error 1
make[2]: Leaving directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/usr/local/src/openoptimus/trunk/optimusdaemon/plugins/minithree'
make: *** [install-recursive] Error 1

```

Getting better, but still not quite there yet.

---

### Post by SevenMachines on 2012-04-01
if you want to install to /usr/local you need *do* need to be root
$ sudo make install

---

### Post by Keith_Beef on 2012-04-01
> **SevenMachines said:**
> if you want to install to /usr/local you need *do* need to be root
$ sudo make install

Yes, that worked. Thanks again.

I now have /usr/local/bin/optimusdaemon, but need to figure out how to make use of it.

---

