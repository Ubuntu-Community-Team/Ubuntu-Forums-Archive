---
title: "Trying to compile a SDL C++ program for windows with mingw and g++"
date: 2007-06-27
forum: Programming Talk
---

### Post by gingi on 2007-06-27
Hello there, I've installed the mingw32 package from Synaptic and I am trying to compile a Windows version of a SDL program I wrote in C++. (I'm using Feisty)
This is the command I'm trying to use:
i586-mingw32msvc-g++  block.cpp -o block.exe `sdl-config --cflags --libs`
However, I get the following errors:
/usr/include/SDL/SDL_stdinc.h:72:20: iconv.h: No such file or directory
/usr/include/SDL/SDL_stdinc.h:165:22: alloca.h: No such file or directory

When I add these two missing files to the command I get even more errors about missing header files needed by the new files.
Is there something I'm missing here? any help will be appreciated. :)

---

### Post by kaamos on 2007-06-27
Have you compiled SDL (and a whole bunch of other libraries that it needs) with mingw? You should have the mingw versions of the libs and headers in /usr/i586-mingw32msvc/

---

### Post by gingi on 2007-06-27
> **kaamos said:**
> Have you compiled SDL (and a whole bunch of other libraries that it needs) with mingw? You should have the mingw versions of the libs and headers in /usr/i586-mingw32msvc/

Hmm... nope :) It does seem obvious now though.
Maybe I should have mentioned I am a newbie to SDL,C++,mingw AND Linux - a dangerous combination.

I think I know how to get the mingw versions of SDL, after all the diffrent guides I went through today.
Thank you for your help!

edit: Well... maybe not...:oops:
How shall I go about doing it?

yet another edit: Got it. :] I downloaded SDL-devel-1.2.11-mingw32.tar.gz from libsdl.com, extracted it, and copied the libs and headers to their place in /usr/i586-mingw32msvc/. Then this command produced a working windows exe:
i586-mingw32msvc-g++ block.cpp -o block.exe -lmingw32 -lSDLmain -lSDL -I/usr/i586-mingw32msvc/include/SDL
I don't if that is what you meant, as I haven't compiled anything, but it seems to work

---

### Post by kendase3 on 2008-02-03
Hey, thanks to your edit I was able to finally run mingw!  I'd looked all over the internet and surprisingly everyone assumed the people trying to use it were total pros, which is certainly not the case for me.  Anyway, just wanted to thank you, and now I'm off to try adding the vital image library among others to my mingw setup.

---

### Post by kendase3 on 2008-02-03
Hmm, could anyone give me a hint as to what specialized mingw command I must use to add libraries now that I've manually added all the respective libraries' files in the same respective folders in the SDL one already included?  I got the win32 dev versions of each library, but I'm getting error messages "no such file or directory."

edit:  alright, fixed that one, now the error i receive is 

(using this command)":~/cproj/proj1$ i586-mingw32msvc-g++ proj1.cc -o proj1.exe -lmingw32 -lSDLmain -lSDL-l/usr/i586-mingw32msvc/include/SDL

In file included from /usr/lib/gcc/i586-mingw32msvc/3.4.5/include/c++/backward/iostream.h:31,
                 from proj1.cc:14:
/usr/lib/gcc/i586-mingw32msvc/3.4.5/include/c++/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/usr/lib/gcc/i586-mingw32msvc/3.4.5/../../../../i586-mingw32msvc/bin/ld: cannot find -lSDL-l/usr/i586-mingw32msvc/include/SDL
collect2: ld returned 1 exit status"

This file definitely runs with the included libraries in Ubuntu and I checked the include path to make sure it was identical; it is.  Any ideas?

---

### Post by CC_machine on 2008-08-04
the problem is the "-l/usr/i586-mingw32msvc/include/SDL" needs to be "-I/usr/i586-mingw32msvc/include/SDL" - an uppercase "I" not a lowercase "L". also there needs to be spaces between -lSDL and -I/usr/i586-mingw32msvc/include/SDL. to use SDL_image, SDL_ttf etc just use -lSDL_image, -lSDL_ttf etc.

i hope this helps, even though that post was a long while ago ^_^

---

