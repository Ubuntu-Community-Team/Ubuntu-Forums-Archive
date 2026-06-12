---
title: "Glut"
date: 2009-02-01
forum: Programming Talk
---

### Post by coachabower on 2009-02-01
I have been instructed to install linux to develop some c++ code for a class.  I have ubuntu installed and working great.  The glut lib I am supposed to use is located here:
[www.opengl.org/resources/libraries/glut/](www.opengl.org/resources/libraries/glut/)

When I extract the files I follow the readme found in the folder labeled "linux".  The file instructs me to replace the glut.cf file found in the main directory with a modified version found in the linux folder.  After doing so it instructs me to run the command ./mkmkfiles.imake.  When I do so I get the error
bash: ./mkmkfiles.imake: /bin/csh: bad interpreter: No such file or directory

According to Synaptic I have openGL installed with a glut library, but I'm so new to this that I don't know how to compile the sample code (found below) and tell it to find the already installed version of glut.  And I can't get the version used by the instructor installed either.  

If anyone can help me out I would be eternally grateful.


[http://www.cs.fit.edu/~eribeiro/teaching/cse2050/plotting3d_code.zip](http://www.cs.fit.edu/~eribeiro/teaching/cse2050/plotting3d_code.zip)

---

### Post by skullmunky on 2009-02-01
Don't download and compile GLUT from scratch, using the package from the repositories will be much cleaner in the long run.  Did you install libglut3-dev also?  That's the package that has the header files, e.g. GL/glut.h.

that demo should compile no problem, although it doesn't do much, it looks like, it just opens a window.  build it like this:

```

make -f makefile_image

```

if the makefile's not named specifically "Makefile" you have to use the -f flag.

---

### Post by geirha on 2009-02-01
Whenever you want to compile and link something against a library, you need the -dev-package for that library. In the case of compiling agains glut, then search for glut and -dev
```
aptitude search glut.*-dev
```

In this case, libglut3-dev looks most promising, so [install](apt:libglut3-dev) that
```

$ make -f makefile_image
makefile_image:123: make.dep: No such file or directory
touch main_image.d
touch demoImageWindow.d
touch glutMaster.d
touch glutWindow.d
cat main_image.d demoImageWindow.d glutMaster.d glutWindow.d > make.dep
g++ -g -MMD -c main_image.cpp
main_image.cpp: In function ‘int main()’:
main_image.cpp:34: warning: deprecated conversion from string constant to ‘char*’
g++ -g -MMD -c demoImageWindow.cpp
g++ -g -MMD -c glutMaster.cpp
glutMaster.cpp: In constructor ‘GlutMaster::GlutMaster()’:
glutMaster.cpp:15: warning: deprecated conversion from string constant to ‘char*’
g++ -g -MMD -c glutWindow.cpp
g++ -g  -o gmImageExample     main_image.o demoImageWindow.o glutMaster.o  glutWindow.o   -lglut -lGLU -lGL -lXmu -lXext -lX11 -lm
[color=red]/usr/bin/ld: cannot find -lXmu[/color]
collect2: ld returned 1 exit status
make: *** [gmImageExample] Error 1

```
Now it was unable to find a lib called Xmu, so search for that in the same way
```
aptitude search xmu.*-dev
...
sudo aptitude install libxmu-dev
...
$ make -f makefile_image  # Should compile and link now
$ ./gmImageExample

```

---

### Post by coachabower on 2009-02-02
excellent, thank you, I will try it when I get home.  Apparently the whole class has been having trouble because the instructor extended the deadline a full month.  After I get glut installed I should be able to hammer out the code, simple c++ assignment to display a 3d graph.

---

