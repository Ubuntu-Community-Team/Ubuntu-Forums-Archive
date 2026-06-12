---
title: "Libraries under Netbeans"
date: 2008-08-11
forum: Programming Talk
---

### Post by LXXXIII on 2008-08-11
Hey, I'm trying to use SDL with Netbeans and C++. I have added the directory **/usr/include/SDL** in the general linker options, but it gives problems with a test program:

```

[......]In function `main':
~/NetBeansProjects/SDL-test/main.cc:5: undefined reference to `SDL_Init'
~/NetBeansProjects/SDL-test/main.cc:8: undefined reference to `SDL_Quit'[....]
```What is exactly the deal with the directory structure if it's about Linux and libraries?

---

### Post by StOoZ on 2008-08-12
how does the exact include looks like? (of SDL)

---

### Post by LXXXIII on 2008-08-12
/usr/include/SDL is:

```
total 580K
-rw-r--r-- 1 root root 4.3K 2008-01-05 05:52 begin_code.h
-rw-r--r-- 1 root root 1.4K 2008-01-05 05:52 close_code.h
-rw-r--r-- 1 root root 1.9K 2008-01-05 05:52 SDL_active.h
-rw-r--r-- 1 root root  11K 2008-01-05 05:52 SDL_audio.h
-rw-r--r-- 1 root root  910 2008-01-05 05:52 SDL_byteorder.h
-rw-r--r-- 1 root root 5.6K 2008-01-05 05:52 SDL_cdrom.h
-rw-r--r-- 1 root root 8.8K 2008-01-05 05:52 SDL_config.h
-rw-r--r-- 1 root root 2.3K 2008-01-05 05:52 SDL_cpuinfo.h
-rw-r--r-- 1 root root 5.6K 2008-01-05 05:52 SDL_endian.h
-rw-r--r-- 1 root root 1.8K 2008-01-05 05:52 SDL_error.h
-rw-r--r-- 1 root root  13K 2008-01-05 05:52 SDL_events.h
-rw-r--r-- 1 root root  910 2008-01-05 05:52 SDL_getenv.h
-rw-r--r-- 1 root root 3.1K 2008-01-05 05:52 SDL.h
-rw-r--r-- 1 root root 5.1K 2008-01-05 05:52 SDL_joystick.h
-rw-r--r-- 1 root root 3.8K 2008-01-05 05:52 SDL_keyboard.h
-rw-r--r-- 1 root root 7.0K 2008-01-05 05:52 SDL_keysym.h
-rw-r--r-- 1 root root 2.8K 2008-01-05 05:52 SDL_loadso.h
-rw-r--r-- 1 root root 2.7K 2008-01-05 05:52 SDL_main.h
-rw-r--r-- 1 root root 4.5K 2008-01-05 05:52 SDL_mouse.h
-rw-r--r-- 1 root root 5.6K 2008-01-05 05:52 SDL_mutex.h
-rw-r--r-- 1 root root  183 2008-01-05 05:52 SDL_name.h
-rw-r--r-- 1 root root 329K 2008-01-05 05:52 SDL_opengl.h
-rw-r--r-- 1 root root 2.5K 2008-01-05 05:52 SDL_platform.h
-rw-r--r-- 1 root root 1.9K 2008-01-05 05:52 SDL_quit.h
-rw-r--r-- 1 root root 4.7K 2008-01-05 05:52 SDL_rwops.h
-rw-r--r-- 1 root root  16K 2008-01-05 05:52 SDL_stdinc.h
-rw-r--r-- 1 root root 5.9K 2008-01-05 05:52 SDL_syswm.h
-rw-r--r-- 1 root root 4.4K 2008-01-05 05:52 SDL_thread.h
-rw-r--r-- 1 root root 4.4K 2008-01-05 05:52 SDL_timer.h
-rw-r--r-- 1 root root  910 2008-01-05 05:52 SDL_types.h
-rw-r--r-- 1 root root 2.5K 2008-01-05 05:52 SDL_version.h
-rw-r--r-- 1 root root  37K 2008-01-05 05:52 SDL_video.h

```FWIW, that's pretty much the only SDL dir I can find.

---

### Post by Zugzwang on 2008-08-12
:-) This is not what StOoZ meant.

1. He/She wants to know your settings in Netbeans and the *complete* output of a compiling process, including the commands for compiling that Netbeans actually invoked.

2. If you add /usr/include/SDL in the general linker options you are doing something wrong. The include path has to be added to the compiler options and the libraries path is for the linker options. Furthermore you might have to put "-I" in front of the directory for include directories or "-L" for linking directories, respectively.

3. Finally, adding the directory is not enough. You also need to tell the linker to actually link the library. From the command line, you add "-lSDL" as an option to the linker. We don't know Netbeans, so you've got to find the equivalent.

---

### Post by LXXXIII on 2008-08-12
Thanks. I had a hunch it wasn't exactly what was meant :)

** 1.** To address the first point, this is shown with compilation:
```
Running "rm -rf build/Debug/GNU-Linux-x86/main.o" in ~/NetBeansProjects/SDL-test


Clean successful. Exit value 0.

Running "/usr/bin/make -f nbproject/Makefile-Debug.mk build/Debug/GNU-Linux-x86/main.o" in ~/NetBeansProjects/SDL-test

mkdir -p build/Debug/GNU-Linux-x86
g++    -c -g -o build/Debug/GNU-Linux-x86/main.o main.cc

Build successful. Exit value 0.
```I thought it was alright.

During the building of the whole project, this is what is shown:
```
/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `~/NetBeansProjects/SDL-test'
mkdir -p dist/Debug/GNU-Linux-x86
g++     -o dist/Debug/GNU-Linux-x86/sdl-test build/Debug/GNU-Linux-x86/main.o -L/usr/include 
build/Debug/GNU-Linux-x86/main.o: In function `main':
~/NetBeansProjects/SDL-test/main.cc:5: undefined reference to `SDL_Init'
~/NetBeansProjects/SDL-test/main.cc:8: undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
make[1]: *** [dist/Debug/GNU-Linux-x86/sdl-test] Error 1
make[1]: Leaving directory `~/NetBeansProjects/SDL-test'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.
```I hope these complete messages provide sufficient information.
[B]
2.[/B] To address the second point, I have now added the include directory under the general C++  compiler options. There is a field to specify command line options, but as it is now it seems Netbeans should take care of it itself (as it provides the -l flag).

** 3.** The equivalent in Netbeans seems to be under **Linker | General | Additional Libraries**. I really don't know where those exact libraries are, so yeah.... that's where I'm stuck.

---

### Post by Zugzwang on 2008-08-12
> **LXXXIII said:**
> ** 3.** The equivalent in Netbeans seems to be under **Linker | General | Additional Libraries**. I really don't know where those exact libraries are, so yeah.... that's where I'm stuck.

What you are trying to do is to link "/usr/lib/libSDL.so" against your program. Normally, you should try to add "-lSDL" to the linker options. It should then appear in the "g++" line in your linking output. Avoid using the precise paths wherever possible, the "/usr/lib" directory is automatically added to the search directories for libraries.

---

### Post by LXXXIII on 2008-08-12
Ah! Great stuff! Thanks :) I added **-lSDL** to the command line options inside Netbeans.

But unfortunately, now I get ALSA errors when trying to run the program. Grrrrr.....

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

```
I've troubleshooted this ALSA sound stuff before, but I never got it to work.

---

### Post by Zugzwang on 2008-08-12
That looks like a configuration problem not connected to programming at all. See the respective forums and google for help.

---

### Post by joag on 2010-02-02
Maybe the topic is outdated at this point but I had the same problem with the round function and the linker didn't know how to link the math library to my code, what you need to do is just to right click the project select properties, select your compiler (c in my case) and under command line additional options link to your library (in my case -lm).

joag

---

