---
title: "[SOLVED] Unable to build any KDevelop project C++ (complete noob)"
date: 2008-06-20
forum: Programming Talk
---

### Post by Predator106 on 2008-06-20
Hello, I'm a complete noob to any non-Microshaft development environments, and I decided to go with KDevelop and the SDL library, to do game programming, this is in C++ by the way.
So I tried creating a new project as one guide had pointed out, to support that library, but unfortunately I couldn't build it. So I figured OK, I'll create a standard C++ project, which should surely build successfully. I was wrong.

Here is the error that I get, I have not modified anything really(unless you count colors :) ).

I hope nobody gets mad or anything about the size of the screenie. I just wanted it to display what was going on basically. And by the way, I have wordwrap in the output window.

To simplify it for you, this is what it says:

cd '/home/shaun/Programming/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/shaun/Programming/test/debug' && cd '/home/shaun/Programming/test/debug' && CXXFLAGS="-O0 -g3" "/home/shaun/Programming/test/configure" --enable-debug=full && cd '/home/shaun/Programming/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

Hopefully you guys can help me figure out what is wrong.




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=74752&stc=1&d=1213973281[/IMG]

---

### Post by geirha on 2008-06-20
I've never used kdevelop, but the error message says it can't find the aclocal program. aclocal is part of the [automake](apt:automake) package, so installing that package should fix that error.

---

### Post by diaa on 2008-06-20
GCC(the compiler) doesn't come with ubuntu so you have to install it manually, I think that's what you need.
To install the compiler and required tools:
```
sudo apt-get install essential make
```

also you may need the packages *autoconf automake* so install then also
```
sudo apt-get install automake autoconf
```

---

### Post by Predator106 on 2008-06-20
Well the first one doesn't work, it says no such package 'essential'.
The second one did work and download stuff, but then this made me realize that I was missing dependencies for KDevelop, so I found their page and am installing them now... Hopefully it will work perfectly.

---

### Post by diaa on 2008-06-20
sorry, it was supposed to be
```
sudo apt-get install build-essential make
```

---

### Post by WW on 2008-06-20
> **diaa said:**
> sorry, it was supposed to be
```
sudo apt-get install build-essential make
```
[build-essential](http://packages.ubuntu.com/hardy/build-essential) depends on **make**, so you don't have to explicitly list **make**; apt-get will do that for you (but there is no harm in including it).

---

### Post by Predator106 on 2008-06-20
Oh Okay. The only problem is now, it seems that the compiler/linker can't find SDL. But the thing is, it shows no problems with the #include "SDL/SDL.h".

The problem is when it comes across SDL commands like...SDL_INIT_AUDIO
It says that it can't find it. I am using the template from KDevelop for SDL, so it should be bug free code...

cd '/home/shaun/Programming/SDL_Test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make 
make all-recursive
Making all in src
linking sdl_test (g++)
linking sdl_test (g++)
sdl_test.o: In function `main':
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:37: undefined reference to `SDL_Init'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:38: undefined reference to `SDL_GetError'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:39: undefined reference to `SDL_Quit'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:43: undefined reference to `SDL_CDNumDrives'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:45: undefined reference to `SDL_CDName'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:44: undefined reference to `SDL_CDNumDrives'
/home/shaun/Programming/SDL_Test/src/sdl_test.cpp:48: undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
make[2]: *** [sdl_test] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I didn't mess with any of the linker options or anything either...Could that be the problem?

---

### Post by diaa on 2008-06-20
you need SDL libraries:
```
sudo apt-get install libsdl-dev 
```

---

### Post by diaa on 2008-06-20
> **diaa said:**
> you need SDL libraries:
```
sudo apt-get install libsdl-dev 
```

Oh, you said it compiles properly so I think you have the headers and the libraries , you need to tell the compiler to link with SDL libraries, the following command returns the options that should be passed to the compiler to link with SDL libraries

```
pkg-config sdl --libs--cflags 
```

so if compiling manually you do the following:
```
gcc -o app app.cpp `pkg-config sdl --libs--cflags`
```

notice that these are backticks, it makes the terminal evaluate the command in between and replace it with its output so it becomes
```
gcc -o app app.cpp <output of pkg-config sdl --libs--cflags>
```

you need to figure out how to do this in KDevelop but it shouldn't be hard

---

### Post by Predator106 on 2008-06-21
YES!! YES!! Man, you have no idea how grateful I am, the solution now outputs to the console.

Just FYI, and in case someone ever has this same problem, and happens to be searching for it or something, to get it working I did the following in KDevelop.

(in system terminal)

pkg-config sdl --libs --cflags

For me, it returned the following:

-D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/SDL  -lSDL  

I then did the following:

Project-> Project Options :: Configure Options :: C++.Compiler Flags(CXXFLAGS)

I just appended the line I got from the terminal at the end of the textbox.

Thanks so much everyone, now I should finally be able to continue learning C++, and try out and learn SDL.

---

### Post by Can+~ on 2008-06-21
Please learn how to compile with the command line before jumping with IDEs. That knowledge will make you a better programmer, you can compile it on almost any *nix OS even without an IDE (or a GUI frontend for that matter), and get a deeper knowledge on how compiler works, and how to use them properly.

---

### Post by Predator106 on 2008-06-21
Okay, I'll think about it.

---

### Post by tito.112 on 2008-07-25
> **diaa said:**
> Oh, you said it compiles properly so I think you have the headers and the libraries , you need to tell the compiler to link with SDL libraries, the following command returns the options that should be passed to the compiler to link with SDL libraries

```
pkg-config sdl --libs--cflags 
```

so if compiling manually you do the following:
```
gcc -o app app.cpp `pkg-config sdl --libs--cflags`
```

notice that these are backticks, it makes the terminal evaluate the command in between and replace it with its output so it becomes
```
gcc -o app app.cpp <output of pkg-config sdl --libs--cflags>
```

you need to figure out how to do this in KDevelop but it shouldn't be hard

I have problem with the that : pkg-config sdl --libs--cflags , it gives me that error report : tito112@tito112-desktop:~$ pkg-config sdl --libs--cflags
--libs--cflags: unknown option

please help me in that error , I can't run a program .
and the Kdevelop gives me this error : konsole --workdir '/home/tito112/Desktop/essam/debug/./src' -e /bin/sh -c '/home/tito112/Desktop/essam/debug/./src/essam ; echo "Press Enter to continue!";read dummy'
/bin/sh: konsole: not found
*** Exited with status: 127 ***

---

### Post by geirha on 2008-07-25
> **tito.112 said:**
> tito112@tito112-desktop:~$ pkg-config sdl --libs--cflags
--libs--cflags: unknown option


There should be a space between the two options --libs and --cflags
```
pkg-config sdl --libs --cflags
```

---

