---
title: "How to change GCC Naming Conventions?"
date: 2014-12-08
forum: Programming Talk
---

### Post by willie6 on 2014-12-08
EDIT:  Original Post is way, way off, I am a watchmaker and a ludite.

I have been attempting to compile openGL code in qt creator and in the terminal using the gcc command in the terminal.  I get the error undefined reference with every single line of 'glfw...' code.

Apparently the problem is GCC has strict naming conventions and does a search for [COLOR=#ff0000]glfw3.dll.a[/COLOR].  It finds something else because the file it's suppsed to find is named [COLOR=#ff0000]glfw3dll.a[/COLOR], and a simple renaming will supposedly make it find the right thing.

My paticular problem is I'm new to linux and I just don't know what i'm looking for and how to look for it.  I am terrible at navigating linux I don't know where to find something.
[B]
How does one go in to change the naming conventions in GCC so it searches for glfw3dll.a or rename the file it needs to find?

[/B]

I will now finish this thread with something that makes me happy.  I built my computer over the weekend and it took me a really long time figure out execute a .run program which I needed to install Nvidia drivers on.  Before I installed drivers, I ran the Valley Benchmark deal that shows all those fancy graphics of a nature because I wanted to see the before and after results.  I got 5 fps running drivers off nouveau x server.  After Nvidia drivers installed the valley program got 50 fps and that made me happy.

---

### Post by TheFu on 2014-12-08
Update the makefile - use something like -l/full/path/to/glfw3dll.a

Linux (and almost all UNIXen) want libraries to be named "lib{something}.so" or "lib{something}.a". Then you can just specify the directory with -L and {something} with -l leaving off the lib and .a/.so parts.  Don't fight it.  Having .dll in the name is poor practice, IMHO.  Leave Windows behind.

BTW, it isn't gcc - it is the unix-way regardless of compiler, language, platform.  Once you get this stuff understood, pretty much any UNIX platform, including Linux, works the same way.  UNIX systems are development platforms from the start.  Using 3 terminals is how I worked back when I did coding for a living.
* editor
* make
* debugger
Just moving the mouse between these would let me change from building, debugging or editing.

---

### Post by willie6 on 2014-12-08
Checking out the make file.  Give me 6 hours to learn more about make files.

6 hours later

I understand your windows way statement now.  I don't think the glfw3dll files exist on linux.  I was confused because winodws, mac-os and linux all have the same exact problem with installing GLFW3 and I just assumed this was a problem unique to linux.

I believe the linux file I'm interested in is libglfw3.a.  I'm going through the makefiles.  I'm beginning to get an idea how the cmake works and understand why making changes to that is better or safer.

Thanks for your comments

---

### Post by willie6 on 2014-12-09
Everything I did in order

1. I unpackaged the glfw3 in downloads.

2. I made a direcectory /home/willie/OpenGL-Build I input cmake -G "Unix Makefiles" /home/willie/Downloads/
3. in the OpenGL-Build I typed make
4.  Sudo make install - terminal output gave me the following  (doing all  this fixed the header in my program after I changed it to #include  <GLFW/glfw3.h>)

> 
-- Install configuration: ""
-- Installing: /usr/local/include/GLFW
-- Up-to-date: /usr/local/include/GLFW/glfw3.h
-- Up-to-date: /usr/local/include/GLFW/glfw3native.h
-- Up-to-date: /usr/local/lib/cmake/glfw/glfwConfig.cmake
-- Up-to-date: /usr/local/lib/cmake/glfw/glfwConfigVersion.cmake
-- Up-to-date: /usr/local/lib/cmake/glfw/glfwTargets.cmake
-- Up-to-date: /usr/local/lib/cmake/glfw/glfwTargets-noconfig.cmake
-- Installing: /usr/local/lib/pkgconfig/glfw3.pc
-- Up-to-date: /usr/local/lib/libglfw3.a


I  can make changes to the make files in my OpenGL-Build directory and  "sudo make install" which will update all the files it installed.

So  the Makefile I was supposed to update with something like  -l/full/path/to/glfw3dll.a, which in my case would be  -l/usr/local/lib/libglfw3.a.

Is the Makefile I'm supposed to update the file that is literally called Makefile or is it another?

---

### Post by steeldriver on 2014-12-09
I'm finding it very hard to understand exactly what you're asking - are you having problems compiling/installing GLFW, or problems compiling a program that uses GLFW?

If the latter, are you using cmake, or some other build system? or are you using gcc from the command line? what are the exact commands you are using, and the exact error(s) that you are getting? Specifics would really help here

---

### Post by willie6 on 2014-12-09
I installed glfw with cmake.  I get undefined references everytime I try to compile in QT creator and in the terminal.
> 
willie@Grapes:~/Downloads/OpenGL-tutorial_v0014_33/tutorial01_first_window$  [COLOR=#ff0000]gcc tutorial01.o[/COLOR]
tutorial01.o: In function `main':
tutorial01.cpp text+0x5): undefined reference to `glfwInit'
tutorial01.cpp text+0x45): undefined reference to `glfwWindowHint'
tutorial01.cpp text+0x54): undefined reference to `glfwWindowHint'
tutorial01.cpp text+0x63): undefined reference to `glfwWindowHint'
tutorial01.cpp text+0x72): undefined reference to `glfwWindowHint'
tutorial01.cpp text+0x91): undefined reference to `glfwCreateWindow'
tutorial01.cpp text+0xc7): undefined reference to `glfwTerminate'
tutorial01.cpp text+0xe0): undefined reference to `glfwMakeContextCurrent'
tutorial01.cpp text+0xe5): undefined reference to `glewInit'
tutorial01.cpp text+0x12f): undefined reference to `glfwSetInputMode'
tutorial01.cpp text+0x148): undefined reference to `glClearColor'
tutorial01.cpp text+0x157): undefined reference to `glfwSwapBuffers'
tutorial01.cpp text+0x15c): undefined reference to `glfwPollEvents'
tutorial01.cpp text+0x170): undefined reference to `glfwGetKey'
tutorial01.cpp text+0x184): undefined reference to `glfwWindowShouldClose'
tutorial01.cpp text+0x19d undefined reference to `glfwTerminate'
collect2: error: ld returned 1 exit status
willie@Grapes:~/Downloads/OpenGL-tutorial_v0014_33/tutorial01_first_window$ 


I'm probably missing something very simple here.

---

### Post by steeldriver on 2014-12-09
You're not telling it which libraries to link - try adding

```

-lglfw -lGLEW

```

to your command line. Also isn't it C++? in which case you should be using g++ not gcc. This worked for me (doing the compile and link in one step):

```

g++ -o tutorial01 tutorial01.cpp -lglfw -lGLEW

```

You could also use pkg-config, as suggested in the GLFW documentation --> [www.glfw.org/docs/latest/build.html#build_link_cmake_pkgconfig]("http://www.glfw.org/docs/latest/build.html#build_link_cmake_pkgconfig")

```

g++ -o tutorial01 `pkg-config --cflags glfw3` tutorial01.cpp `pkg-config --libs glfw3` -lGLEW

```

You may wish to modify the GLFW cmake configuration to build shared libs (the default seems to be not to do so):

```

$ cmake -LH .. | grep -i shared
// Build shared libraries
BUILD_SHARED_LIBS:BOOL=OFF

cmake -DBUILD_SHARED_LIBS=ON ..

```

---

### Post by willie6 on 2014-12-14
QT Creator automatically generates makefiles when a new project made, that makefile is where linkers can be added for whatever code you're trying to compile.

To add linkers I add in the -lglfw3 linkers, like you said I needed, directly into the makefile.  Which looks like this.

> 
LFLAGS        = -m64 
LIBS          = $(SUBLIBS) [COLOR=#ff0000]-lQt5Core -lGL -lGLU -lglfw3 -ldl -lX11 -lXxf86vm -lXrandr -lpthread -lXi[/COLOR]
AR            = ar cqs


If I didn't link a library or put it before linker it's dependent on, I get an error.  For example if I delete -ldl or put it first in the makefile, I get this error.
> 
error adding symbols: DSO missing from command line                      libdl.so.2
/lib/x86_64-linux-gnu/libdl.so.2

or a copy and paste it  /lib/x86_64-linux-gnu/libdl.so.2:-1: error: error adding symbols: DSO missing from command line

I get a multitude of errors for every link I need, but .so.2 came multiple times.

So far I am 95% successful compiling the tutorial.  The only part of tutorial01 of OpenGL's tutorials is glewInit

> 
if ([COLOR=#ff0000]**glewInit**[/COLOR]() != GLEW_OK) {
        fprintf(stderr, "Failed to initialize GLEW\n");
        return -1;
    }


/home/willie/Programing/Learning/Test/main.cpp:40: error: undefined reference to `glewInit'

That section isn't required and the tutorial compiles fine with out it.  I imagine this is an easier fix.

Thanks for your guys reply thus far.

---

