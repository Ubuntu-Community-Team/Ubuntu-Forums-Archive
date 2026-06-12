---
title: "Argh! Need help cross-compiling"
date: 2006-04-07
forum: Programming Talk
---

### Post by dolson on 2006-04-07
I developed a small app in Anjuta. Works fine on Linux for Linux, but when I try to cross-compile it for Win32, well, no such luck.

The last time I managed to do a cross-compile was back in 2002, and I can't figure it out. I tried searching all over, including these forums. I got some good links and tried the content with no luck.

I installed the mingw32* packages.

I tried configuring it like so:
**./configure --with-msw --target=i586-mingw32msvc --host=i586-mingw32msvc --build=i386-linux**
But this resulted in:
```
...
checking dynamic linker characteristics... Win32 ld.exe
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking target system type... i586-pc-mingw32msvc
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... cross compiling; assumed OK...
yes
checking SDL/SDL_ttf.h usability... no
checking SDL/SDL_ttf.h presence... no
checking for SDL/SDL_ttf.h... no
configure: error: *** Could not find SDL/SDL_ttf.h You must download SDL_image from http://www.libsdl.org/projects/SDL_ttf/ to proceed
```

I tried specifying where the libs and headers are:
**LDFLAGS=-L/opt/SDLlibs/lib CPPFLAGS=-I/opt/SDLlibs/include/ ./configure --with-msw --target=i586-mingw32msvc --host=i586-mingw32msvc --build=i386-linux**
But this results in the same thing as above.

I tried running the export commands:
[b]export CC=i586-mingw32msvc-gcc
export CXX=i586-mingw32msvc-c++
export LD=i586-mingw32msvc-ld
export AR=i586-mingw32msvc-ar
export AS=i586-mingw32msvc-as
export NM=i586-mingw32msvc-nm
export STRIP=i586-mingw32msvc-strip
export RANLIB=i586-mingw32msvc-ranlib
export DLLTOOL=i586-mingw32msvc-dlltool
export OBJDUMP=i586-mingw32msvc-objdump
export RESCOMP=i586-mingw32msvc-windres
./configure
[/b]

But then I get:

```
...
checking for gcc... i586-mingw32msvc-gcc
checking for C compiler default output file name... a.exe
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
```

So I specify it: **./configure --host i386-linux** and then I get the same problem about my SDL_ttf.h file above.

So.. After all this, I updated the build-cross.sh script from libsdl.org and ran it. Then I tried running cross-configure.sh and I get the same SDL_ttf.h error.

I try this:
**LDFLAGS=-L/opt/cross-tools/lib CFLAGS=-I/opt/cross-tools/include /opt/cross-tools/cross-configure.sh**
and the result is different this time:
```
...
checking SDL/SDL_ttf.h usability... yes
checking SDL/SDL_ttf.h presence... no
configure: WARNING: SDL/SDL_ttf.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: SDL/SDL_ttf.h: proceeding with the compiler's result
checking for SDL/SDL_ttf.h... yes
checking SDL/SDL_image.h usability... yes
checking SDL/SDL_image.h presence... no
configure: WARNING: SDL/SDL_image.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: SDL/SDL_image.h: proceeding with the compiler's result
checking for SDL/SDL_image.h... yes
checking SDL/SDL_mixer.h usability... yes
checking SDL/SDL_mixer.h presence... no
configure: WARNING: SDL/SDL_mixer.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: SDL/SDL_mixer.h: proceeding with the compiler's result
checking for SDL/SDL_mixer.h... yes
updating cache cross-config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
```

I have NO idea what those warnings are all about... But anyhow, let's try **make**:
```
...
make[2]: Entering directory `/home/dana/testw32app/src'
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-main.o -MD -MP -MF ".deps/template-main.Tpo" \
          -c -o template-main.o `test -f 'main.cc' || echo './'`main.cc; \
        then mv -f ".deps/template-main.Tpo" ".deps/template-main.Po"; \
        else rm -f ".deps/template-main.Tpo"; exit 1; \
        fi
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-functions.o -MD -MP -MF ".deps/template-functions.Tpo" \
          -c -o template-functions.o `test -f 'functions.cc' || echo './'`functions.cc; \
        then mv -f ".deps/template-functions.Tpo" ".deps/template-functions.Po"; \
        else rm -f ".deps/template-functions.Tpo"; exit 1; \
        fi
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-sprite.o -MD -MP -MF ".deps/template-sprite.Tpo" \          -c -o template-sprite.o `test -f 'sprite.cc' || echo './'`sprite.cc; \
        then mv -f ".deps/template-sprite.Tpo" ".deps/template-sprite.Po"; \
        else rm -f ".deps/template-sprite.Tpo"; exit 1; \
        fi
/bin/sh ../libtool --mode=link i586-mingw32msvc-c++  -g -O2  -L/opt/cross-tools/lib -o template.exe  template-main.o template-functions.o template-sprite.o -L/usr/lib -lSDL -lpthread -lSDL_ttf -lSDL_image -lSDL_mixer
mkdir .libs
i586-mingw32msvc-c++ -g -O2 -o template.exe template-main.o template-functions.o template-sprite.o  -L/opt/cross-tools/lib -L/usr/lib -L/usr/share/qt3/lib /usr/lib/libSDL_ttf.so /usr/lib/libfreetype.so /usr/lib/libSDL_image.so /usr/lib/libtiff.so /usr/lib/libjpeg.so -lpng -lz -L/usr/X11R6/lib /usr/lib/libSDL_mixer.so /usr/lib/libvorbisfile.so /usr/lib/libvorbis.so /usr/lib/libogg.so /usr/lib/libsmpeg.so -lstdc++ /usr/lib/libSDL.so /usr/lib/libartsc.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so /usr/lib/libglib-2.0.so /usr/lib/libesd.so /usr/lib/libaudiofile.so -laudio -lXt -lXext /usr/lib/libaa.so -lncurses -lslang -lX11 /usr/lib/libasound.so -lm -ldl -lpthread
/usr/lib/libSDL_ttf.so: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
make[2]: *** [template.exe] Error 1
make[2]: Leaving directory `/home/dana/testw32app/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dana/testw32app'
make: *** [all] Error 2
```

No go. So then I clean and try with **/opt/cross-tools/cross-make.sh**:
```
...
Making all in src
make[2]: Entering directory `/home/dana/testw32app/src'
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-main.o -MD -MP -MF ".deps/template-main.Tpo" \
          -c -o template-main.o `test -f 'main.cc' || echo './'`main.cc; \
        then mv -f ".deps/template-main.Tpo" ".deps/template-main.Po"; \
        else rm -f ".deps/template-main.Tpo"; exit 1; \
        fi
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-functions.o -MD -MP -MF ".deps/template-functions.Tpo" \
          -c -o template-functions.o `test -f 'functions.cc' || echo './'`functions.cc; \
        then mv -f ".deps/template-functions.Tpo" ".deps/template-functions.Po"; \
        else rm -f ".deps/template-functions.Tpo"; exit 1; \
        fi
if i586-mingw32msvc-c++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/SDL   -Wall -O1 -g -g -O2 -MT template-sprite.o -MD -MP -MF ".deps/template-sprite.Tpo" \          -c -o template-sprite.o `test -f 'sprite.cc' || echo './'`sprite.cc; \
        then mv -f ".deps/template-sprite.Tpo" ".deps/template-sprite.Po"; \
        else rm -f ".deps/template-sprite.Tpo"; exit 1; \
        fi
/bin/sh ../libtool --mode=link i586-mingw32msvc-c++  -g -O2  -L/opt/cross-tools/lib -o template.exe  template-main.o template-functions.o template-sprite.o -L/usr/lib -lSDL -lpthread -lSDL_ttf -lSDL_image -lSDL_mixer
mkdir .libs
i586-mingw32msvc-c++ -g -O2 -o template.exe template-main.o template-functions.o template-sprite.o  -L/opt/cross-tools/lib -L/usr/lib -L/usr/share/qt3/lib /usr/lib/libSDL_ttf.so /usr/lib/libfreetype.so /usr/lib/libSDL_image.so /usr/lib/libtiff.so /usr/lib/libjpeg.so -lpng -lz -L/usr/X11R6/lib /usr/lib/libSDL_mixer.so /usr/lib/libvorbisfile.so /usr/lib/libvorbis.so /usr/lib/libogg.so /usr/lib/libsmpeg.so -lstdc++ /usr/lib/libSDL.so /usr/lib/libartsc.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so /usr/lib/libglib-2.0.so /usr/lib/libesd.so /usr/lib/libaudiofile.so -laudio -lXt -lXext /usr/lib/libaa.so -lncurses -lslang -lX11 /usr/lib/libasound.so -lm -ldl -lpthread
/usr/lib/libSDL_ttf.so: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
make[2]: *** [template.exe] Error 1
make[2]: Leaving directory `/home/dana/testw32app/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dana/testw32app'
make: *** [all] Error 2
```

I have no idea what I am doing wrong, nor do I know what I did back in 2002 to make it work. Back then, I successfully cross-compiled Battle Pong. But now I can't even get my simple SDL template to cross-compile.

Any and all help is very much appreciated.

Thanks.

---

### Post by toojays on 2006-04-07
Your final link command:```
i586-mingw32msvc-c++ -g -O2 -o template.exe template-main.o template-functions.o template-sprite.o  -L/opt/cross-tools/lib -L/usr/lib -L/usr/share/qt3/lib /usr/lib/libSDL_ttf.so /usr/lib/libfreetype.so /usr/lib/libSDL_image.so /usr/lib/libtiff.so /usr/lib/libjpeg.so -lpng -lz -L/usr/X11R6/lib /usr/lib/libSDL_mixer.so /usr/lib/libvorbisfile.so /usr/lib/libvorbis.so /usr/lib/libogg.so /usr/lib/libsmpeg.so -lstdc++ /usr/lib/libSDL.so /usr/lib/libartsc.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so /usr/lib/libglib-2.0.so /usr/lib/libesd.so /usr/lib/libaudiofile.so -laudio -lXt -lXext /usr/lib/libaa.so -lncurses -lslang -lX11 /usr/lib/libasound.so -lm -ldl -lpthread
```
is mixing native libraries and cross-compiled libraries. You mustn't have any native libraries on this line.

It doesn't look like the configure process for the program you are trying to compile knows how to build a Windows binary. If it did, it wouldn't be trying to link against X. I suspect that you have taken the "--with-msw" argument of your ./configure from another forum post. This argument works for wxWidgets, but it isn't necessarily going to work for any other package. From the looks of it, your best bet is to probably tell your configure process to use your cross-compiled sdl-config rather than your native one.

Good luck.

---

### Post by dolson on 2006-04-07
Well, thanks for your reply. Unfortunately, I am too stupid to do this or something. When I try using the other sdl-config, I am told my C compiler cannot create executables.

I am ready to give up I think..

---

### Post by dolson on 2006-04-08
Okay, so I didn't surrender yet... But, I'm not successful yet either. So. Here is where I am at:

I decide to forget about autogen, configure and all that, and I'm writing my own Makefile. Here is one that works for g++:

```
CFLAGS=-W -Wall -O2 -ggdb `sdl-config --cflags`
LIBS=-lm `sdl-config --libs` -lSDL_image -lSDL_ttf -lSDL_mixer
OBJS=functions.o sprite.o main.o
CC=g++
OUTPUT=tioli

default: clean all

PHONY: clean run default

clean:
        @echo Cleaning...
        rm -f $(OUTPUT) $(OBJS)
        rm -f *~
        @echo Done.

run: clean all
        @echo Runing...
        wine ./$(OUTPUT)

all: $(OBJS)
        $(CC) $(CFLAGS) $(OBJS) -o $(OUTPUT) $(LIBS)

main.o:  main.cc main.h functions.h sprite.h
        $(CC) $(CFLAGS) -c main.cc

sprite.o: sprite.cc sprite.h
        $(CC) $(CFLAGS) -c sprite.cc

functions.o: functions.cc functions.h
        $(CC) $(CFLAGS) -c functions.cc
```

That works, if I run make, it compiles for Linux. OK. As I understand the cross-tools from libsdl.org, I should only have to run cross-make.sh, but it doesn't work, I get this:

```
dana@polly:~/Projects/template/src$ /opt/cross-tools/cross-make.sh -f Makefile.gcc
Cleaning...
rm -f tioli functions.o sprite.o main.o
rm -f *~
Done.
g++ -W -Wall -O2 -ggdb `sdl-config --cflags` -c functions.cc
g++ -W -Wall -O2 -ggdb `sdl-config --cflags` -c sprite.cc
g++ -W -Wall -O2 -ggdb `sdl-config --cflags` -c main.cc
main.cc:14: warning: unused parameter 'argc'
main.cc:14: warning: unused parameter 'argv'
g++ -W -Wall -O2 -ggdb `sdl-config --cflags` functions.o sprite.o main.o -o tioli -lm `sdl-config --libs` -lSDL_image -lSDL_ttf -lSDL_mixer
functions.o: In function `_Z9loadImagePci':/home/dana/Projects/template/src/functions.cc:10: undefined reference to `_IMG_Load'
:/home/dana/Projects/template/src/functions.cc:13: undefined reference to `_SDL_DisplayFormat'
:/home/dana/Projects/template/src/functions.cc:14: undefined reference to `_SDL_FreeSurface'
:/home/dana/Projects/template/src/functions.cc:21: undefined reference to `_SDL_FreeSurface'
functions.o: In function `_Z11unloadImageP11SDL_Surface':/home/dana/Projects/template/src/functions.cc:32: undefined reference to `_SDL_FreeSurface'
functions.o: In function `_Z17restoreBackgroundP11SDL_SurfaceP8SDL_Rect':/home/dana/Projects/template/src/functions.cc:40: undefined reference to `_SDL_UpperBlit'
functions.o: In function `_Z8putImageP11SDL_Surfaceii':/home/dana/Projects/template/src/functions.cc:50: undefined reference to `_SDL_UpperBlit'
sprite.o:/home/dana/Projects/template/src/sprite.cc:111: undefined reference to `_SDL_UpperBlit'
sprite.o:/home/dana/Projects/template/src/sprite.cc:83: undefined reference to `_SDL_GetTicks'
sprite.o:/home/dana/Projects/template/src/sprite.cc:87: undefined reference to `_SDL_GetTicks'
main.o: In function `_Z11deinitStuffv':/home/dana/Projects/template/src/main.cc:155: undefined reference to `_TTF_CloseFont'
:/home/dana/Projects/template/src/main.cc:156: undefined reference to `_SDL_Delay'
:/home/dana/Projects/template/src/main.cc:157: undefined reference to `_SDL_Quit'
:/home/dana/Projects/template/src/main.cc:158: undefined reference to `_TTF_Quit'
main.o: In function `_Z10initScreenv':/home/dana/Projects/template/src/main.cc:171: undefined reference to `_SDL_Flip'
main.o: In function `_Z9initVideov':/home/dana/Projects/template/src/main.cc:179: undefined reference to `_SDL_Init'
:/home/dana/Projects/template/src/main.cc:185: undefined reference to `_SDL_WM_SetCaption'
:/home/dana/Projects/template/src/main.cc:188: undefined reference to `_SDL_SetVideoMode'
:/home/dana/Projects/template/src/main.cc:190: undefined reference to `_SDL_GetError'
:/home/dana/Projects/template/src/main.cc:180: undefined reference to `_SDL_GetError'
main.o: In function `_Z10initCursorv':/home/dana/Projects/template/src/main.cc:201: undefined reference to `_SDL_ShowCursor'
:/home/dana/Projects/template/src/main.cc:206: undefined reference to `_SDL_WarpMouse'
main.o: In function `_Z8initFontv':/home/dana/Projects/template/src/main.cc:214: undefined reference to `_TTF_Init'
:/home/dana/Projects/template/src/main.cc:221: undefined reference to `_TTF_OpenFont'
:/home/dana/Projects/template/src/main.cc:223: undefined reference to `_SDL_GetError'
:/home/dana/Projects/template/src/main.cc:215: undefined reference to `_SDL_GetError'
main.o: In function `SDL_main':/home/dana/Projects/template/src/main.cc:27: undefined reference to `_SDL_PumpEvents'
:/home/dana/Projects/template/src/main.cc:28: undefined reference to `_SDL_GetMouseState'
:/home/dana/Projects/template/src/main.cc:29: undefined reference to `_SDL_GetKeyState'
:/home/dana/Projects/template/src/main.cc:32: undefined reference to `_SDL_GetMouseState'
:/home/dana/Projects/template/src/main.cc:47: undefined reference to `_SDL_GetMouseState'
:/home/dana/Projects/template/src/main.cc:63: undefined reference to `_TTF_RenderText_Solid'
:/home/dana/Projects/template/src/main.cc:79: undefined reference to `_SDL_Flip'
:/home/dana/Projects/template/src/main.cc:80: undefined reference to `_SDL_Delay'
:/home/dana/Projects/template/src/main.cc:43: undefined reference to `_SDL_WarpMouse'
/opt/cross-tools/lib/gcc/i386-mingw32msvc/3.4.5/../../../../i386-mingw32msvc/lib/libmingw32.a(main.o):main.c:(.text+0x106): undefined reference to `_WinMain@16'
collect2: ld returned 1 exit status
make: *** [all] Error 1
```

So for whatever reason, the cross-make.sh script doesn't do what I think it should do. Maybe it's how I built my Makefile, I don't know. So anyhow, I modified the Makefile to use the mingw stuff:

```
CFLAGS=-W -Wall -O2 -ggdb `/opt/SDL-1.2.9/bin/sdl-config --cflags`
LIBS=-lm `/opt/SDL-1.2.9/bin/sdl-config --libs` -lSDL_image -lSDL_ttf -lSDL_mixer
OBJS=functions.o sprite.o main.o
CC=i586-mingw32msvc-g++
OUTPUT=tioli.exe

default: clean all

PHONY: clean run default

clean:
        @echo Cleaning...
        rm -f $(OUTPUT) $(OBJS)
        rm -f *~
        @echo Done.

run: clean all
        @echo Runing...
        wine ./$(OUTPUT)

all: $(OBJS)
        $(CC) $(CFLAGS) $(OBJS) -o $(OUTPUT) $(LIBS)

main.o:  main.cc main.h functions.h sprite.h
        $(CC) $(CFLAGS) -c main.cc

sprite.o: sprite.cc sprite.h
        $(CC) $(CFLAGS) -c sprite.cc

functions.o: functions.cc functions.h
        $(CC) $(CFLAGS) -c functions.cc
```

So I try that:

```
dana@polly:~/Projects/template/src$ make -f Makefile.mingw
Cleaning...
rm -f tioli functions.o sprite.o main.o
rm -f *~
Done.
i586-mingw32msvc-g++ -W -Wall -O2 -ggdb `/opt/SDL-1.2.9/bin/sdl-config --cflags` -c functions.cc
In file included from functions.cc:1:
functions.h:5:17: SDL.h: No such file or directory
functions.h:6:21: SDL_ttf.h: No such file or directory
functions.h:7:23: SDL_image.h: No such file or directory
functions.h:8:23: SDL_mixer.h: No such file or directory
In file included from functions.cc:1:
functions.h:11: error: expected constructor, destructor, or type conversion before '*' token
functions.h:11: error: expected `,' or `;' before '*' token
functions.h:12: error: variable or field `unloadImage' declared void
functions.h:12: error: `SDL_Surface' was not declared in this scope
functions.h:12: error: `tmpSrf' was not declared in this scope
functions.h:13: error: variable or field `restoreBackground' declared void
functions.h:13: error: `SDL_Surface' was not declared in this scope
functions.h:13: error: `tmpSrf' was not declared in this scope
functions.h:13: error: `SDL_Rect' was not declared in this scope
functions.h:13: error: `tmpRect' was not declared in this scope
functions.h:13: error: initializer expression list treated as compound expression
functions.h:14: error: variable or field `putImage' declared void
functions.h:14: error: `SDL_Surface' was not declared in this scope
functions.h:14: error: `tmpSrf' was not declared in this scope
functions.h:14: error: expected primary-expression before "int"
functions.h:14: error: expected primary-expression before "int"
functions.h:14: error: initializer expression list treated as compound expression
functions.h:17: error: expected init-declarator before '*' token
functions.h:17: error: expected `,' or `;' before '*' token
functions.cc:5: error: expected constructor, destructor, or type conversion before '*' token
functions.cc:5: error: expected `,' or `;' before '*' token
functions.cc:30: error: variable or field `unloadImage' declared void
functions.cc:30: error: redefinition of `int unloadImage'
functions.h:12: error: `int unloadImage' previously defined here
functions.cc:30: error: `SDL_Surface' was not declared in this scope
functions.cc:30: error: `tmpSrf' was not declared in this scope
functions.cc:31: error: expected `,' or `;' before '{' token
functions.cc:38: error: variable or field `restoreBackground' declared void
functions.cc:38: error: redefinition of `int restoreBackground'
functions.h:13: error: `int restoreBackground' previously defined here
functions.cc:38: error: `SDL_Surface' was not declared in this scope
functions.cc:38: error: `tmpSrf' was not declared in this scope
functions.cc:38: error: `SDL_Rect' was not declared in this scope
functions.cc:38: error: `tmpRect' was not declared in this scope
functions.cc:39: error: expected `,' or `;' before '{' token
functions.cc:45: error: variable or field `putImage' declared void
functions.cc:45: error: redefinition of `int putImage'
functions.h:14: error: `int putImage' previously defined here
functions.cc:45: error: `SDL_Surface' was not declared in this scope
functions.cc:45: error: `tmpSrf' was not declared in this scope
functions.cc:45: error: expected primary-expression before "int"
functions.cc:45: error: expected primary-expression before "int"
functions.cc:46: error: expected `,' or `;' before '{' token
make: *** [functions.o] Error 1
```

I get the exact same output if I use the cross-make.sh script as far as I can tell, so I don't know... I think I am closer now, but I am unsure why it can't find the libs.. Any ideas?

Thanks in advance! :D

---

### Post by dolson on 2006-04-08
Okay, I fixed my makefile and directory layout and such, and boy, I got results! I also had not changed a variable in the sdl-config script (which I don't currently use anyhow).

So, yes, I have success now! And I *WILL* be documenting the process for everyone else, and I will link to it in this thread once I am done.

Thanks for your patience and suggestions to me!

---

### Post by toojays on 2006-04-08
Congratulations.

I hope your experience will serve you well in the future.

---

### Post by dolson on 2006-04-08
Okay, here is my documentation: [http://icculus.org/~dolson/sdl/](http://icculus.org/~dolson/sdl/)

Hope it helps someone else some day.

---

