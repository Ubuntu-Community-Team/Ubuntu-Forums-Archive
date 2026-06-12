---
title: "SDL dependency madness"
date: 2008-04-29
forum: Programming Talk
---

### Post by HyperHacker on 2008-04-29
So far this is what I've managed to hack together in the makefile to get a program using libSDL to compile, but I hate how it smells:
```
# Program info
PROGRAM = mk64view
OPTIONS =
SHARED = ../shared/
SHARED_OBJS = compat.o debugout.o filex.o mathx.o mio0.o sdlx.o stringsx.o timex.o
SHARED_SRCS = $(SHARED)compat.cpp $(SHARED)compat.h $(SHARED)debugout.c $(SHARED)debugout.h $(SHARED)filex.cpp $(SHARED)filex.h $(SHARED)mathx.cpp $(SHARED)mathx.h $(SHARED)mio0.c $(SHARED)mio0.h $(SHARED)sdlx.cpp $(SHARED)sdlx.h $(SHARED)stringsx.cpp $(SHARED)stringsx.h $(SHARED)timex.cpp $(SHARED)timex.h
OBJS = $(SHARED_OBJS) clsMK64.o clsN64RSP.o events.o video.o main.o
OTHER_DEP =
LIBS = $(LIBPATH)libSDLmain.a $(LIBPATH)libSDL.a $(LIBPATH)libGL.so $(LIBPATH)libasound.so.2 $(LIBPATH)libartsc.so.0 $(LIBPATH)libesd.so.0 $(LIBPATH)libaudio.so.2 $(LIBPATH)libdirectfb-0.9.so.25 $(LIBPATH)libaa.so.1

CMDLINE = $(PROGRAM)
LIBPATH = /usr/lib/
DELETE = rm -f
#export PATH := $(MINGW)bin:$(PATH)
OS = LINUX

# etc
CXX = g++
CXXFLAGS = -O3 -Wall -I$(SHARED) -DDEBUG_FILENAME=\"$(PROGRAM)_debug.log\" -D$(OS)#-DWINVER=0x500 -D_WIN32_WINNT=0x501 -D_WIN32_IE=0x0500
LD = ${CXX}
LDFLAGS =
COMPILE = $(CXX) $(CXXFLAGS) -c

all: $(PROGRAM)
	@echo @@ START @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	@./$(CMDLINE)
	@echo @@ END @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

noexec: $(PROGRAM)

.PHONY : all noexec clean

$(PROGRAM): $(OBJS)
	$(LD) $(LDFLAGS) -o $(PROGRAM) $(OBJS) $(LIBS) $(OPTIONS)

#dialog.o: dialog.res
#	windres -v -o dialog.o "$(CURDIR)\dialog.res"

%.o: %.c $(OTHER_DEP)
	$(COMPILE) $(<) -o $(@)

$(SHARED_OBJS): $(SHARED_SRCS)
	$(COMPILE) $(^)

clean:
	$(DELETE) $(PROGRAM)
	$(DELETE) *.o
	$(DELETE) *.log


```(This is hacked together with no real knowledge of how to make a makefile, and ported from the makefile for the Windows version, so yeah it sucks. <_<) Since upgrading to Hardy this isn't working:
```
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `PULSE_CloseAudio':
(.text+0x17e): undefined reference to `pa_simple_drain'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `PULSE_CloseAudio':
(.text+0x18e): undefined reference to `pa_simple_free'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `PULSE_PlayAudio':
(.text+0x1dc): undefined reference to `pa_simple_write'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `Audio_Available':
(.text+0x301): undefined reference to `pa_simple_new'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `Audio_Available':
(.text+0x30f): undefined reference to `pa_simple_free'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `PULSE_OpenAudio':
(.text+0x429): undefined reference to `pa_channel_map_init_auto'
/usr/lib/libSDL.a(SDL_pulseaudio.o): In function `PULSE_OpenAudio':
(.text+0x51c): undefined reference to `pa_simple_new'
```and my usual method of Googling the error message to see what library I need to pile on is getting me nowhere. (I really don't get why a program that doesn't use sound needs so many sound libraries in the first place... <_<)

Then again, I wonder if the upgrade didn't just break gcc, given the hundreds of lines of "warning: deprecated conversion from string constant to ‘char*’" from a program that compiled with no warnings at all before and worked just fine. Like what, I'm supposed to explicitly cast every single constant string? That could get annoying quick. (Not to mention, some of these lines don't even have strings on them!)

I get the idea there must be some "common" library I'm supposed to link against that includes all of these or something instead of this libfoobar-0.9.so-42 nonsense?

[edit] I grep'd for the string in /usr/lib and found "libpulse-simple.so.0" was what I needed to add, but this still seems like a terrible way to do it...filename)

---

### Post by RIchard James13 on 2008-04-29
This may be a dumb question but you do have the pulse audio dev package installed don't you?

Because that is what it seems to be asking for. If not can you supply some more info, actually a lot more info. What program? Why do you say it doesn't use sound when it needs it to compile? etc? etc?

---

### Post by HyperHacker on 2008-04-29
Apparently I do; I found libpulse-simple.so.0 and added it to the pile and it compiles again. This is a program I'm making, it doesn't do anything involving sound, but it seems like SDL requires a bunch of sound libraries even if you don't use them.

---

### Post by RIchard James13 on 2008-04-29
> **HyperHacker said:**
> This is a program I'm making, it doesn't do anything involving sound, but it seems like SDL requires a bunch of sound libraries even if you don't use them.

Glad you got the library problem fixed. I just ran ldd on my SDL game and all it comes up with is
```
$ ldd spacemonster
	linux-gate.so.1 =>  (0xb7f25000)
	libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0xb7f08000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7e79000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e41000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7e1e000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7e09000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7d16000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cf0000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7ce5000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b96000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7b76000)
	libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7b23000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb7a60000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a5b000)
	libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0xb79f8000)
	libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0xb79f0000)
	libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0xb79dd000)
	/lib/ld-linux.so.2 (0xb7f26000)

```

Which means it is only linked to asound but I only had to tell the linker SDL and SDL_image.

---

### Post by Lux Perpetua on 2008-04-29
Strange, I've never had trouble getting something to compile with SDL. My compile line is usually **g++ -lSDL -lSDL_image ...**.

---

### Post by RIchard James13 on 2008-04-29
With the GCC warnings the compiler has been upgraded. [this page]("http://babbage.cs.qc.edu/courses/cs701/Writeable_Strings.html") explains why that warning is necessary. I just fixed in my code all those warnings. I did it by replacing, in every function that receives a literal string as "char *" with "const char*" instead. Because if you pass a string like this foo("bar"); then the compiler assumes the string is constant and complains if foo is declared as foo(char *someString).

---

