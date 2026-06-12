---
title: "setting up SDL problem"
date: 2007-04-12
forum: Programming Talk
---

### Post by gzhj on 2007-04-12
Hi. I was trying to install SDL, but encountered problems.

I followed [lazy foo's instruction]("http://lazyfoo.net/SDL_tutorials/lesson01/linux/cli/index.php") and downloaded this package - SDL-devel-1.2.11-1.i386.rpm. But as it is a rpm package, I could not install it directly. So I followed [this ]("http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html"), installed alien and converted the rpm to deb, then installed the deb package. But when I was trying to compile lazy foo's testing file using "g++ -o myprogram mysource.cpp -lSDL", the problem came out. I got this in the terminal:

[COLOR="SeaGreen"]gzhj@zhengjin:~/package$ sudo dpkg -i sdl-devel_1.2.11-1_i386.deb 
(Reading database ... 106764 files and directories currently installed.)
Preparing to replace sdl-devel 1.2.11-1 (using sdl-devel_1.2.11-1_i386.deb) ...
Unpacking replacement sdl-devel ...
Setting up sdl-devel (1.2.11-1) ...
gzhj@zhengjin:~/package$ g++ -o test test.cpp -lSDL
g++: test.cpp: No such file or directory
gzhj@zhengjin:~/package$ cd /home/gzhj/Desktop/
gzhj@zhengjin:~/Desktop$ g++ -o test test.cpp -lSDL
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_alsa_audio.o): In function `UnloadALSALibrary':
(.text+0x1a): undefined reference to `dlclose'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_alsa_audio.o): In function `LoadALSALibrary':
(.text+0x4d): undefined reference to `dlopen'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_alsa_audio.o): In function `LoadALSALibrary':
(.text+0x95): undefined reference to `dlvsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_alsa_audio.o): In function `LoadALSALibrary':
(.text+0xb3): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_systhread.o): In function `SDL_SYS_CreateThread':
(.text+0x60): undefined reference to `pthread_create'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_systhread.o): In function `SDL_SYS_SetupThread':
(.text+0xce): undefined reference to `pthread_sigmask'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_systhread.o): In function `SDL_SYS_WaitThread':
(.text+0x12d): undefined reference to `pthread_join'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_systhread.o): In function `SDL_SYS_KillThread':
(.text+0x141): undefined reference to `pthread_cancel'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_CreateSemaphore':
(.text+0x2c): undefined reference to `sem_init'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_DestroySemaphore':
(.text+0x7a): undefined reference to `sem_destroy'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_SemTryWait':
(.text+0xa2): undefined reference to `sem_trywait'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_SemWait':
(.text+0xd6): undefined reference to `sem_wait'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_SemValue':
(.text+0x1c7): undefined reference to `sem_getvalue'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_syssem.o): In function `SDL_SemPost':
(.text+0x1f3): undefined reference to `sem_post'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysmutex.o): In function `SDL_CreateMutex':
(.text+0x29): undefined reference to `pthread_mutexattr_init'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysmutex.o): In function `SDL_CreateMutex':
(.text+0x39): undefined reference to `pthread_mutexattr_settype'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_UnloadLibrary':
(.text+0x530): undefined reference to `dlclose'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x5c9): undefined reference to `dlopen'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x5f6): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x60f): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x628): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x641): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary':
(.text+0x65a): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_x11gl.o):(.text+0x673): more undefined references to `dlsym' follow
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_LoadObject':
(.text+0x17): undefined reference to `dlopen'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_LoadObject':
(.text+0x1e): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_LoadFunction':
(.text+0x63): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_LoadFunction':
(.text+0xb5): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_LoadFunction':
(.text+0xc0): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libSDL.a(SDL_sysloadso.o): In function `SDL_UnloadObject':
(.text+0xe6): undefined reference to `dlclose'
collect2: ld returned 1 exit status
[/COLOR]

I am new to Ubuntu and SDL. Can someone kindly tell me how can I solve this problem? Thank you.

---

### Post by WW on 2007-04-13
I haven't used SDL, but I don't think you should have to install it following those instructions.  I'm pretty sure it is already packaged and available in Ubuntu's repositories.  Installing the package  **libsdl1.2-dev** is probably a good start. 

Perhaps some folks more experienced with SDL can elaborate.

---

### Post by Wybiral on 2007-04-13
Why did you manually install it? It's in the repositories...


This command should do it:
```

sudo apt-get install build-essential libsdl1.2-dev

```

You may also want these two (image and font loader):
```

sudo apt-get install libsdl-image1.2-dev libsdl-ttf2.0-dev

```

---

