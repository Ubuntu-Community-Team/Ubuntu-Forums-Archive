---
title: "Cross Compilation for Windows using Glib and Allegro"
date: 2010-03-20
forum: Programming Talk
---

### Post by JDShu on 2010-03-20
Hey all, I've been trying to figure out all day how to get mingw compiler to use the glib and allegro libraries that I installed under ubuntu. If I simply replace gcc in my makefile with i586-mingw32msvc-gcc, I just get a lot of undefined references for glib and allegro. I'm probably being naive, but I have no idea where I need to start to solve this problem.

---

### Post by pholding on 2010-03-20
If you're getting undefined references then it means that there is a problem linking the objects produced by the compiler to one or more libraries. Would you be able to post the error messages?

---

### Post by JDShu on 2010-03-20
Yeah I figured its a problem with linking the libraries, I just have no idea how to fix it.

Heres the beginning chunk of the errors (it goes on and on, and the allegro errors are further down)


```
/usr/lib/liballeg.a(umodules.o): In function `_unix_load_modules':
(.text+0x2f3): warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linkingmain.o:main.c:(.text+0x2d): undefined reference to `_g_free'
main.o:main.c:(.text+0x32): undefined reference to `_g_free'
main.o:main.c:(.text+0x37): undefined reference to `_g_str_equal'
main.o:main.c:(.text+0x3c): undefined reference to `_g_str_hash'
main.o:main.c:(.text+0x41): undefined reference to `_g_hash_table_new_full'
main.o:main.c:(.text+0x57): undefined reference to `_pack_fopen'
main.o:main.c:(.text+0x94): undefined reference to `_g_strdup'
main.o:main.c:(.text+0xb2): undefined reference to `_g_malloc'
main.o:main.c:(.text+0xbe): undefined reference to `_g_strtod'
main.o:main.c:(.text+0xd0): undefined reference to `_g_hash_table_insert'
main.o:main.c:(.text+0xec): undefined reference to `_pack_fgets'
main.o:main.c:(.text+0x106): undefined reference to `_pack_fclose'
main.o:main.c:(.text+0x14b): undefined reference to `___errno_location'
main.o:main.c:(.text+0x15d): undefined reference to `__install_allegro_version_check'
main.o:main.c:(.text+0xd): undefined reference to `_g_hash_table_destroy'
```And heres my Makefile, critique on it is welcome too, since I'm pretty new to it all and I'm sure it doesn't conform to standards.

```
flags =  -v `allegro-config --cflags` `alogg-config --cflags` `alogg-config --libs` `pkg-config --cflags --libs glib-2.0`

visnovel: main.o node.o commands.o parser.o
    i586-mingw32msvc-gcc main.o node.o commands.o parser.o -o visnovel $(flags)

main.o: main.c node.h
    i586-mingw32msvc-gcc -c main.c $(flags)

node.o: node.c node.h
    i586-mingw32msvc-gcc -c node.c $(flags)

commands.o: commands.c node.h
    i586-mingw32msvc-gcc -c commands.c $(flags)

parser.o: parser.c node.h
    i586-mingw32msvc-gcc -c parser.c $(flags)

clean:
    rm -f visnovel *.o
```

---

### Post by SledgeHammer_999 on 2010-03-20
You probably have to compile the respective libraries with mingw and then point mingw to them instead of the system's(linux version).

---

### Post by JDShu on 2010-03-20
> **SledgeHammer_999 said:**
> You probably have to compile the respective libraries with mingw and then point mingw to them instead of the system's(linux version).

Ohhh I see its a conceptual issue that I failed to realize. I'll try that  now. Thanks!

---

### Post by roccivic on 2010-03-20
I think other people have already done that, don't double up on the effort. I ported zenity to win last year and had to resolve a huge mess of dependencies, but didn't have to compile many libraries.

Good places to look for libs are:
[http://ftp.gnome.org/pub/GNOME/binaries/win32/](http://ftp.gnome.org/pub/GNOME/binaries/win32/)
[http://gnuwin32.sourceforge.net/packages.html](http://gnuwin32.sourceforge.net/packages.html)
[http://www.google.com/](http://www.google.com/)

---

### Post by JDShu on 2010-03-21
Thanks to roccivic for the links, I followed the directions [here]("http://ricardo.ecn.wfu.edu/%7Ecottrell/cross-gtk/") for glib and then did something similar for allegro. However now I have a compiler problem apparently with libiconv?

```
/tmp/ccmkGFs7.o:main.c:(.text+0x0): multiple definition of `_init_game_state'
/tmp/ccco0KU3.o:main.c:(.text+0x0): first defined here
/tmp/ccmkGFs7.o:main.c:(.text+0x133): multiple definition of `_close_game_state'
/tmp/ccco0KU3.o:main.c:(.text+0x133): first defined here
/tmp/ccmkGFs7.o:main.c:(.text+0x14c): multiple definition of `__mangled_main'
/tmp/ccco0KU3.o:main.c:(.text+0x14c): first defined here
/tmp/ccmkGFs7.o:main.c:(.text+0x19f): multiple definition of `_WinMain@16'
/tmp/ccco0KU3.o:main.c:(.text+0x19f): first defined here
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lintl
collect2: ld returned 1 exit status
make: *** [main.o] Error 1
```

and heres my makefile:

```
CC = i586-mingw32msvc-gcc -Wall -mms-bitfields -mwindows
PKG_CONFIG_PATH = /usr/i586-mingw32msvc/lib/pkgconfig

CFLAGS := $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_PATH) \
          pkg-config --cflags glib-2.0)
LIBS := $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_PATH) \
          pkg-config --libs glib-2.0) -I/usr/i586-mingw32msvc/include/allegro -I/usr/i586-mingw32msvc/lib/

visnovel.exe: main.o node.o commands.o parser.o
     $(CC) main.o node.o commands.o parser.o -o visnovel $(CFLAGS) $< $(LIBS)

main.o: main.c node.h
    $(CC) main.c $(CFLAGS) $< $(LIBS)

node.o: node.c node.h
    $(CC) node.c $(CFLAGS) $< $(LIBS)

commands.o: commands.c node.h
    $(CC) commands.c $(CFLAGS) $< $(LIBS)

parser.o: parser.c node.h
    i586-mingw32msvc-gcc -c parser.c $(CFLAGS) $< $(LIBS)

clean:
    rm -f visnovel *.o

```

Any ideas?

I'm heading off to bed now, thanks again to everyone for their help! At the very least, I'm learning something about cross compilation.

---

### Post by roccivic on 2010-03-21
I did say that it will be a pain resolving dependencies...
libiconv is here: [http://gnuwin32.sourceforge.net/packages/libiconv.htm](http://gnuwin32.sourceforge.net/packages/libiconv.htm)

You might want to look here, too: [http://www.gtk.org/download-windows.html](http://www.gtk.org/download-windows.html)
There is an all-in-one bundle there. With some luck most dependencies that you need are already resolved there and other individual packages are at least preconfigured for win32.

Peace

---

### Post by JDShu on 2010-03-22
Thanks so much guys. After spending my weekend trying to get Allegro to work nicely (it actually started working to some extent except for alogg), I've decided to switch to SDL, because I'm having an easier time getting cross compiling to work for it since sdl_mixer seems to be better maintained than alogg (which looks all but abandoned).

Heres the link I used to easily get SDL working:

[http://icculus.org/~dolson/sdl/](http://icculus.org/~dolson/sdl/)

---

### Post by JDShu on 2010-03-25
Alright, the above link got SDL working, but none of the other SDL libraries. The easiest way to set things up was actually by using the mingw-cross-env script provided by the [awesome people here]("http://www.nongnu.org/mingw-cross-env/#tutorial"). I followed the instructions to the letter and now it at least compiles my test programs. However I've hit another snag. When using SDL_mixer, the compiled program (through wine, but testing on Windows it appears to be the same) does not work... at the first Mix_OpenAudio call, I get:

```
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0080: stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"04090409", 0001: stub!
err:ntdll:RtlpWaitForCriticalSection section 0x569fc0 "?" wait timed out in thread 0009, blocked by 0000, retrying (60 sec)

```Here is my Makefile:

```
CROSS=/opt/mingw/usr/bin/i686-pc-mingw32-
CC=$(CROSS)gcc
LD=$(CROSS)ld
AR=$(CROSS)ar

PKG=/opt/mingw/usr/bin/i686-pc-mingw32-pkg-config

CFLAGS=`$(PKG) --cflags sdl SDL_mixer glib-2.0`
LIBS=`$(PKG) --libs sdl SDL_mixer glib-2.0` 

SOURCES =    music.c

all:        vnovel.exe

clean:
        rm -f *.o
        rm vnovel.exe

vnovel.exe:    ${SOURCES}
        ${CC} -Wl,--subsystem,windows -Wall ${CFLAGS} -o vnovel.exe ${SOURCES} ${LIBS}
```Does anybody see something wrong, or has anybody tried using SDL_mixer through the mingw-cross-env script?

---

### Post by JDShu on 2010-03-26
bump... is this problem too obscure? Anybody ever manage to make a cross compiling environment using SDL and SDL_mixer with ogg support?

---

