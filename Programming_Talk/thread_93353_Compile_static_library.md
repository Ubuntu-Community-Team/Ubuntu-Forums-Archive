---
title: "Compile static library"
date: 2005-11-21
forum: Programming Talk
---

### Post by series on 2005-11-21
I have created a static library. Imaginative as I am, I call it "library.a". It is an archive containing all the object files of my library, which is actually just one file: library.o

Now I'm not sure how to link this library into my program, and I'm not sure of how to configure where g++ searches for libs. I really don't want to install my library on the filesystem, I want to link it into my program from the current dir.

The relevant files are: "main.cpp", "library.a", "library.o", "library.h", "library.cpp".

How do I compile main.cpp so that it can use the functions in library?

---

### Post by Retrix on 2005-11-21
g++ -c main.cpp
g++ main.o library.a -o main

should do the trick.

---

### Post by series on 2005-11-21
Alright. That was just too easy :cool: 

It first didn't work for me because I reversed the order to g++: first library and then main (which seemed more logical for some reason). Then I was unsure if g++ could even handle the archive by itself... well, thanks, it works fine now.

---

### Post by saritha123 on 2007-09-13
i had compiled and runned the gnash version 7, now i had all .so files,
from all .o i build .a files ,now how can i link  this libraries so tht i can run gnash can u help me.

i had the files libgnashgui.a ,all gnash files .o into . a i made, can u help how to link and run gnash using this static same idea as u impemented can u suggest me some idea

thanks

---

### Post by dwhitney67 on 2007-09-13
> **series said:**
> Alright. That was just too easy :cool: 

It first didn't work for me because I reversed the order to g++: first library and then main (which seemed more logical for some reason). Then I was unsure if g++ could even handle the archive by itself... well, thanks, it works fine now.

The ordering of the library(-ies) is important.  When the linker is processing the object files and detects an unresolved function, it tries later to find it in a library.  If it can't, then the build will fail due to undefined references.

There are cases when one library (e.g. libB) is dependent upon a another (e.g. libA).  Thus, when linking, libA would have to be specified *before* libB.  At least that's how I remember it to be.  'gcc' has evolved a lot in the last couple of years so maybe that's not true anymore.  But I do recall issues with circular dependencies (a strong clue that a bad design has been implemented).

By the way, you may want to rename your library to a more conventional form.  Generally the name of the library begins with the prefix "lib".  Thus an example would be libfoo.a (or libfoo.so).

When compiling/linking, the statement could look like:

[FONT="Courier New"]$ g++ myFile.cpp -L../libs -lfoo[/FONT]

The -L option indicates a path to search for user-defined or 3rd-party libraries, and the -l is used to define which library to reference (read).  The usage of "foo" above is the correct syntax.  The linker knows to prefix that name with "lib", and it will deduce whether it is a dot-a or dot-so file (within ../libs).

---

### Post by dwhitney67 on 2007-09-13
> **saritha123 said:**
> i had compiled and runned the gnash version 7, now i had all .so files,
from all .o i build .a files ,now how can i link  this libraries so tht i can run gnash can u help me.

i had the files libgnashgui.a ,all gnash files .o into . a i made, can u help how to link and run gnash using this static same idea as u impemented can u suggest me some idea

thanks

Please see the comments I posted to 'series'.  Let me know if you still require assistance.

---

### Post by saritha123 on 2007-09-17
> **dwhitney67 said:**
> Please see the comments I posted to 'series'.  Let me know if you still require assistance.


can u tell me exact command how to link this .a libraries and run gnash

---

### Post by dwhitney67 on 2007-09-17
The best thing to do is create a Makefile, one for the library and another for the application.

Here's an example of one for the library:

```

#
# File:  Makefile (for library)
#
CC=gcc
LIB=libGnash.a
LIBDEST=./

LIBSRC=abc.c def.c

LIBOBJ=$(LIBSRC:.c=.o)

install: $(LIB)
<tab>@echo lib Makefile - installing $(LIB)
<tab>@install -m 444 $(LIB) $(LIBDEST)

$(LIB): $(LIBOBJ)
<tab>@echo lib Makefile - archiving $(LIB)
<tab>@$(AR) r $(LIB) $(LIBOBJ)

.c.o:
<tab>@echo lib Makefile - compiling $<
<tab>@$(CC) $(CFLAGS) -c $< -o $@
```


Then for the application:

```

#
# File:  Makefile for application
#
CC=gcc
LIBDIR=../lib
LIBS=-lGnash

SRC=app_abc.c app_def.c

OBJS=$(SRC:.c=.o)

EXE=myapp

all: $(EXE)

$(EXE): $(OBJS)
<tab>@echo application Makefile - linking $<
<tab>@$(CC) $^ $(LIBDIR) $(LIBS) -o $@

.c.o:
<tab>@echo application Makefile - compiling $<
<tab>@$(CC) $(CFLAGS) -c $< -o $@
```

Wherever you see <tab>, replace that with a tab-character.  Of course, modify the names of the source files, where you want your library installed, etc.

You can also consider adding other things to the Makefile, but for now I think what I have given will get you going.

Btw, if you are developing a C++ application, modify CC to be g++, and in lieu of CFLAGS use CXXFLAGS.

Please let me know if you still have questions.


P.S. Edited for readability.

---

### Post by dwhitney67 on 2007-09-17
> **saritha123 said:**
> can u tell me exact command how to link this .a libraries and run gnash

If you want to type the command in the command-line to link, then here's an example:

[FONT="Courier New"]gcc file1.c file2.c -L./ -lGnash -o myapp[/FONT]

The file1.c and file2.c are the application modules.

The -L is used to specify the path where libGnash.a resides.

The -l is used to specify the library that will be linked with the application files.  Note that the 'lib' and the file extension of the library are not required in the name.

The -o is to direct the linker to create the executable with the name provided.  Without the -o, the resulting executable would be called a.out.

---

### Post by saritha123 on 2007-09-17
actually i had all .a files now i have to link this files so tht gnash can run,

using  this command 


[COLOR="Black"][B][SIZE="5"]arm_v5t_le-ar rc  libgnashbackend.a .libs/render_handler_tri.o .libs/render_handler_agg.o [/COLOR][/B[/SIZE]]


i  created  all .a file example libgnashgui.a,libgnashserver.a
 like this i had all .a files so how can i link this files so tht gnash can run


can u help me out
 urgent

---

### Post by saritha123 on 2007-09-17
actually i am running htis command so that it can create gnash

arm_v5t_le-g++ -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -o gnash  ./libgnashgui.a ../libamf/libgnashamf.a ../backend/libgnashbackend.a ../server/libgnashserver.a ../server/asobj/.libs/libgnashasobjs.a /home/saritha/arm/gnash/libamf/libgnashamf.a -L/home/saritha/arm/LibSourceForGnash/jpeg/jpeg-6b -L/home/saritha/arm/LibSourceForGnash/zlib/zlibinstall -L/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -L/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/lib -L/home/saritha/arm/LibSourceForGnash/png/pnginstall/lib -L/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib /home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib/libogg.a /home/saritha/arm/gnash/libbase/libgnashbase.a /home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib/libcurl.a /opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib//libstdc++.so ../libgeometry/libgnashgeo.a ../libbase/libgnashbase.a ./libgnashgui.a -lm -L/home/saritha/arm/LibSourceForGnash/agg/agg-2.4/src -lagg -lpng -ljpeg -lssl -lcrypto -ldl -lX11 -lXi -lz -lrt -Wl,--rpath -Wl,/home/saritha/arm/gnashinstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -Wl,--rpath -Wl,/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/


this all .a is a x-archive which contain  .o files

---

### Post by dwhitney67 on 2007-09-17
I am not sure what you are trying to do.  Your previous post includes the command (in an awful font mind you) the command you issued to create an archive of object files.

Btw, the usage of the 'c' option is not required.  Thus this would suffice:
[FONT="Courier New"]
$ arm_v5t_le-ar r libgnashbackend.a <list of object files...>[/FONT]

To link an application that uses this archive library, issue a command similar to the following:

[FONT="Courier New"]$ arm_v5t_le-g++ <list of .cpp files...> -lgnashbackend <-lotherLibraries...> -o appName[/FONT]

Then run your application as such:

[FONT="Courier New"]$ ./appName[/FONT]

If you have other libraries to build with your application, specify them using the "-l" option, and ensure that they are specified in the correct order.  In other words, if library A is dependent on library B, then specify B before A.

---

### Post by dwhitney67 on 2007-09-17
> **saritha123 said:**
> actually i am running htis command so that it can create gnash

arm_v5t_le-g++ -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -o gnash  ./libgnashgui.a ../libamf/libgnashamf.a ../backend/libgnashbackend.a ../server/libgnashserver.a ../server/asobj/.libs/libgnashasobjs.a /home/saritha/arm/gnash/libamf/libgnashamf.a -L/home/saritha/arm/LibSourceForGnash/jpeg/jpeg-6b -L/home/saritha/arm/LibSourceForGnash/zlib/zlibinstall -L/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -L/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/lib -L/home/saritha/arm/LibSourceForGnash/png/pnginstall/lib -L/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib /home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib/libogg.a /home/saritha/arm/gnash/libbase/libgnashbase.a /home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib/libcurl.a /opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib//libstdc++.so ../libgeometry/libgnashgeo.a ../libbase/libgnashbase.a ./libgnashgui.a -lm -L/home/saritha/arm/LibSourceForGnash/agg/agg-2.4/src -lagg -lpng -ljpeg -lssl -lcrypto -ldl -lX11 -lXi -lz -lrt -Wl,--rpath -Wl,/home/saritha/arm/gnashinstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -Wl,--rpath -Wl,/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/


this all .a is a x-archive which contain  .o files

I just saw this post.  You have quite a few libraries to link against!  A nightmare situation if one is dependent on another.

So, anyhow, when you run the command listed above, do you receive an error, or does it succeed?  If an error is returned, what is it?

---

### Post by saritha123 on 2007-09-18
following error i am getting ,can u tell me where is the problem


[saritha@localhost gui]$ arm_v5t_le-g++ -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -o ./.libs/gnash gnash.o  ./libgnashgui.a ../libamf/libgnashamf.a ../backend/libgnashbackend.a ../server/libgnashserver.a ../server/asobj/.libs/libgnashasobjs.a /home/saritha/arm/gnash/libamf/libgnashamf.a -L/home/saritha/arm/LibSourceForGnash/jpeg/jpeg-6b -L/home/saritha/arm/LibSourceForGnash/zlib/zlibinstall -L/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -L/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/home/saritha/arm/LibSourceForGnash/ssl/sslinstall/lib -L/home/saritha/arm/LibSourceForGnash/png/pnginstall/lib -L/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib /home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib/libogg.a /home/saritha/arm/gnash/libbase/libgnashbase.a /home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib/libcurl.a /opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib//libstdc++.so ../libgeometry/libgnashgeo.a ../libbase/libgnashbase.a ./libgnashgui.a -lm -L/home/saritha/arm/LibSourceForGnash/agg/agg-2.4/src -lagg -lpng -ljpeg -lssl -lcrypto -ldl -lX11 -lXi -lz -lrt -Wl,--rpath -Wl,/home/saritha/arm/gnashinstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/ogg/ogginstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/curl/curlinstall/lib -Wl,--rpath -Wl,/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/

./libgnashgui.a(gnash)(.bss+0x1d4): multiple definition of `url'
gnash.o(.bss+0x0):/home/saritha/arm/gnash/gui/gnash.cpp:62: first defined here
./libgnashgui.a(gnash)(.data+0x4): In function `__data_start':
crtstuff.c: multiple definition of `__dso_handle'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/crtbegin.o(.data+0x0): first defined here
./libgnashgui.a(gnash)(.init+0x0): In function `_init':
crtstuff.c: multiple definition of `_init'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/crti.o(.init+0x0):../../gcc/config/arm/crti.asm: first defined here
./libgnashgui.a(gnash)(.text+0x0): In function `_start':
../sysdeps/arm/elf/start.S:71: multiple definition of `_start'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/crt1.o(.text+0x0):../sysdeps/arm/elf/start.S:71: first defined here
./libgnashgui.a(gnash)(.text+0xc4c): In function `main':
/home/saritha/arm/gnash/gui/gnash.cpp:297: multiple definition of `main'
gnash.o(.text+0xbd0):/home/saritha/arm/gnash/gui/gnash.cpp:297: first defined here
./libgnashgui.a(gnash)(.fini+0x0): In function `_fini':
crtstuff.c: multiple definition of `_fini'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/crti.o(.fini+0x0):../../gcc/config/arm/crti.asm: first defined here
./libgnashgui.a(gnash)(.bss+0x1d8): multiple definition of `infile'
gnash.o(.bss+0x4):/home/saritha/arm/gnash/gui/gnash.cpp:62: first defined here
./libgnashgui.a(gnash)(.got+0x0): multiple definition of `_GLOBAL_OFFSET_TABLE_'
./libgnashgui.a(Player.o)(.got.plt+0x0):/home/saritha/arm/gnash/gui/Player.cpp:136: first defined here
./libgnashgui.a(gnash)(.rodata+0x0): multiple definition of `_IO_stdin_used'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/crt1.o(.rodata+0x0):../sysdeps/arm/elf/start.S:71: first defined here
./libgnashgui.a(gnash)(.data+0x0): In function `__data_start':
crtstuff.c: multiple definition of `__data_start'
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../target/usr/lib/crt1.o(.data+0x0):../sysdeps/arm/elf/start.S:71: first defined here
/home/saritha/arm/gnash/libbase/libgnashbase.a(log.o)(.bss+0x0):/home/saritha/arm/gnash/libbase/log.cpp:91: multiple definition of `gnash::dbglogfile'
./libgnashgui.a(gnash)(.bss+0x10): first defined here
/home/saritha/arm/gnash/libbase/libgnashbase.a(log.o)(.bss+0x124):/home/saritha/arm/gnash/libbase/log.cpp:126: multiple definition of `gnash::LogFile::_parserdump'
./libgnashgui.a(gnash)(.bss+0x1d1): first defined here
/home/saritha/arm/gnash/libbase/libgnashbase.a(log.o)(.bss+0x125):/home/saritha/arm/gnash/libbase/log.cpp:126: multiple definition of `gnash::LogFile::_actiondump'
./libgnashgui.a(gnash)(.bss+0x1d0): first defined here
/home/saritha/arm/gnash/libbase/libgnashbase.a(log.o)(.bss+0x128):/home/saritha/arm/gnash/libbase/log.cpp:126: multiple definition of `gnash::LogFile::_verbose'
./libgnashgui.a(gnash)(.bss+0x1cc): first defined here
./libgnashgui.a(Player.o)(.dynamic+0x0): multiple definition of `_DYNAMIC'
../server/libgnashserver.a(ActionExec.o)(.text+0x7d0): In function `gnash::ActionExec::operator()()':
/home/saritha/arm/gnash/server/ActionExec.cpp:159: undefined reference to `gnash::action_buffer::log_disasm(unsigned int) const'
../server/libgnashserver.a(impl.o)(.text+0x87c): In function `gnash::create_movie(tu_file*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
/home/saritha/arm/gnash/server/impl.cpp:392: undefined reference to `gnash::movie_def_impl::movie_def_impl(gnash::create_bitmaps_flag, gnash::create_font_shapes_flag)'
../server/libgnashserver.a(impl.o)(.text+0x88c):/home/saritha/arm/gnash/server/impl.cpp:393: undefined reference to `gnash::movie_def_impl::read(tu_file*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
../server/libgnashserver.a(ASHandlers.o)(.text+0x3f0): In function `gnash::SWF::SWFHandlers::ActionConstantPool(gnash::ActionExec&)':
swf/ASHandlers.cpp:2783: undefined reference to `gnash::action_buffer::process_decl_dict(unsigned int, unsigned int) const'
../server/libgnashserver.a(ASHandlers.o)(.text+0x6210): In function `gnash::SWF::SWFHandlers::ActionPushData(gnash::ActionExec&)':
swf/ASHandlers.cpp:1445: undefined reference to `gnash::action_buffer::read_float_little(unsigned int) const'
../server/libgnashserver.a(ASHandlers.o)(.text+0x6720):swf/ASHandlers.cpp:1499: undefined reference to `gnash::action_buffer::read_double_wacky(unsigned int) const'
../server/libgnashserver.a(tag_loaders.o)(.text+0x3f8): In function `gnash::SWF::tag_loaders::define_shape_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:699: undefined reference to `gnash::shape_character_def::shape_character_def()'
../server/libgnashserver.a(tag_loaders.o)(.text+0x410):swf/tag_loaders.cpp:700: undefined reference to `gnash::shape_character_def::read(gnash::stream*, int, bool, gnash::movie_definition*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x520): In function `gnash::SWF::tag_loaders::define_shape_morph_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:721: undefined reference to `gnash::morph2_character_def::morph2_character_def()'
../server/libgnashserver.a(tag_loaders.o)(.text+0x538):swf/tag_loaders.cpp:722: undefined reference to `gnash::morph2_character_def::read(gnash::stream*, int, bool, gnash::movie_definition*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x79c): In function `gnash::SWF::tag_loaders::sprite_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:1202: undefined reference to `gnash::sprite_definition::sprite_definition(gnash::movie_definition*, gnash::stream*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x824):swf/tag_loaders.cpp:1185: undefined reference to `typeinfo for gnash::movie_def_impl'
../server/libgnashserver.a(tag_loaders.o)(.text+0xa54): In function `gnash::SWF::tag_loaders::button_sound_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:1301: undefined reference to `gnash::button_character_definition::read(gnash::stream*, int, gnash::movie_definition*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0xa9c):swf/tag_loaders.cpp:1292: undefined reference to `typeinfo for gnash::character_def'
../server/libgnashserver.a(tag_loaders.o)(.text+0xaa0):swf/tag_loaders.cpp:1292: undefined reference to `typeinfo for gnash::button_character_definition'
../server/libgnashserver.a(tag_loaders.o)(.text+0xb04): In function `gnash::SWF::tag_loaders::button_character_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:1317: undefined reference to `gnash::button_character_definition::button_character_definition()'
../server/libgnashserver.a(tag_loaders.o)(.text+0xb18):swf/tag_loaders.cpp:1318: undefined reference to `gnash::button_character_definition::read(gnash::stream*, int, gnash::movie_definition*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x1868): In function `gnash::SWF::tag_loaders::define_bits_jpeg2_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/memory:200: undefined reference to `gnash::bitmap_character_def::bitmap_character_def(std::auto_ptr<image::rgb>)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x19f4): In function `gnash::SWF::tag_loaders::define_bits_jpeg_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':

---

### Post by saritha123 on 2007-09-18
continuation


/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/memory:200: undefined reference to `gnash::bitmap_character_def::bitmap_character_def(std::auto_ptr<image::rgb>)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x1c04): In function `gnash::SWF::tag_loaders::define_bits_lossless_2_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/memory:200: undefined reference to `gnash::bitmap_character_def::bitmap_character_def(std::auto_ptr<image::rgba>)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x1c88):/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/memory:200: undefined reference to `gnash::bitmap_character_def::bitmap_character_def(std::auto_ptr<image::rgb>)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x2598): In function `gnash::SWF::tag_loaders::define_bits_jpeg3_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/memory:200: undefined reference to `gnash::bitmap_character_def::bitmap_character_def(std::auto_ptr<image::rgba>)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x2760): In function `gnash::SWF::tag_loaders::define_edit_text_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:1475: undefined reference to `gnash::edit_text_character_def::read(gnash::stream*, int, gnash::movie_definition*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x28d0): In function `gnash::SWF::tag_loaders::define_edit_text_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
../libbase/smart_ptr.h:126: undefined reference to `vtable for gnash::edit_text_character_def'
../server/libgnashserver.a(tag_loaders.o)(.text+0x35a0): In function `gnash::SWF::tag_loaders::do_init_action_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':
swf/tag_loaders.cpp:1521: undefined reference to `gnash::action_buffer::action_buffer()'
../server/libgnashserver.a(tag_loaders.o)(.text+0x35ac):swf/tag_loaders.cpp:108: undefined reference to `gnash::action_buffer::read(gnash::stream*)'
../server/libgnashserver.a(tag_loaders.o)(.text+0x36d4): In function `gnash::SWF::tag_loaders::do_action_loader(gnash::stream*, gnash::SWF::tag_type, gnash::movie_definition*)':

---

### Post by saritha123 on 2007-09-18
./server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x464): In function `gnash::LocalConnection::~LocalConnection()':
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/bits/basic_string.h:418: undefined reference to `gnash::Shm::~Shm()'
../server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x494):/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/bits/basic_string.h:418: undefined reference to `gnash::Shm::~Shm()'
../server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x540): In function `gnash::LocalConnection::~LocalConnection()':
/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/bits/basic_string.h:418: undefined reference to `gnash::Shm::~Shm()'
../server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x570):/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/bin/../lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../target/usr/include/c++/3.4.3/bits/basic_string.h:418: undefined reference to `gnash::Shm::~Shm()'
../server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x5ec): In function `gnash::LocalConnection::LocalConnection()':
/home/saritha/arm/gnash/server/asobj/LocalConnection.cpp:56: undefined reference to `gnash::Shm::Shm()'
../server/asobj/.libs/libgnashasobjs.a(LocalConnection.o)(.text+0x648): In function `gnash::LocalConnection::LocalConnection()':
/home/saritha/arm/gnash/server/asobj/LocalConnection.cpp:56: undefined reference to `gnash::Shm::Shm()'
collect2: ld returned 1 exit status

---

### Post by saritha123 on 2007-09-18
i am getting this errors

---

### Post by saritha123 on 2007-09-18
urgent can u reply

---

### Post by dwhitney67 on 2007-09-18
*> arm_v5t_le-g++ -g -O2 -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -o gnash ./libgnashgui.a ../libamf/libgnashamf.a ../backend/libgnashbackend.a ../server/libgnashserver.a ../server/asobj/.libs/libgnashasobjs.a /home/saritha/arm/gnash/libamf/libgnashamf.a -L/home/saritha/arm/LibSourceForGnash/jpeg/jpeg-6b -L/home/saritha/arm/LibSourceForGnash/zlib/zlibinst all -L/home/saritha/arm/LibSourceForGnash/curl/curlinst all/lib -L/home/saritha/arm/LibSourceForGnash/ssl/sslinstal l/home/saritha/arm/LibSourceForGnash/ssl/sslinstal l/lib -L/home/saritha/arm/LibSourceForGnash/png/pnginstal l/lib -L/home/saritha/arm/LibSourceForGnash/ogg/ogginstal l/lib /home/saritha/arm/LibSourceForGnash/ogg/ogginstall/ lib/libogg.a /home/saritha/arm/gnash/libbase/libgnashbase.a /home/saritha/arm/LibSourceForGnash/curl/curlinsta ll/lib/libcurl.a /opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_le/b in/../target/usr/lib//libstdc++.so ../libgeometry/libgnashgeo.a ../libbase/libgnashbase.a ./libgnashgui.a -lm -L/home/saritha/arm/LibSourceForGnash/agg/agg-2.4/src -lagg -lpng -ljpeg -lssl -lcrypto -ldl -lX11 -lXi -lz -lrt -Wl,--rpath -Wl,/home/saritha/arm/gnashinstall/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/ogg/ogginst all/lib -Wl,--rpath -Wl,/home/saritha/arm/LibSourceForGnash/curl/curlin stall/lib -Wl,--rpath -Wl,/opt/mv_pro_4.0/montavista/pro/devkit/arm/v5t_l e/bin/../target/usr/lib/*

Like I said earlier, when linking so many libraries, one can expect a nightmarish situation like you have posted... thousands of link errors.

All I can suggest is that you try to tackle one at a time, or at least the easy ones.

I noticed that you are specifying libgnashgui.a twice.  There is also a complaint about "main" being referenced (declared) twice.  Find out where main() is defined (actually in which library it is defined), and remove the second occurrence from your list.

Also, if you are using Makefiles, try to eliminate the full path indicating where the libraries are located.  In other words, you should not see something like /home/saritha/arm/LibSourceForGnash in the paths above.  Redefine the paths so that they are relative to the location of the Makefile linking the libraries.

Also check your Makefile for where the following statement resides.  It appears that a -L (and a white space) is missing between sslinstall and the next path; or perhaps a mistake when you copied/pasted the statement?
[I]
-L/home/saritha/arm/LibSourceForGnash/ssl/sslinstal l/home/saritha/arm/LibSourceForGnash/ssl/sslinstal l/lib [/I]

P.S.  In the future, when you post output, select it and mark it up as PHP.

---

