---
title: "[SOLVED] How to install pymunk python physics engine?"
date: 2008-09-06
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-06
So how do I install pymunk python physics engine?

I downloaded pymunk.zip and extracted it. Then I tried to run demo1.py:
```
arho@ohra-laptop:~$ cd Asiakirjat/pymunk-0.1/
arho@ohra-laptop:~/Asiakirjat/pymunk-0.1$ python demo1.py
find_library could not find ChipmunkPyEd
Will try to load ChipmunkPyEd.dll
Loading ChipmunkPyEd.dll failed, will try to load libChipmunkPyEd.so
Traceback (most recent call last):
  File "demo1.py", line 4, in <module>
    import pymunk._chipmunk as cp
  File "/home/arho/Asiakirjat/pymunk-0.1/pymunk/__init__.py", line 6, in <module>
    from pymunk import _chipmunk
  File "/home/arho/Asiakirjat/pymunk-0.1/pymunk/_chipmunk.py", line 15, in <module>
    chiplib = CDLL('libChipmunkPyEd.so')
  File "/usr/lib/python2.5/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libChipmunkPyEd.so: cannot open shared object file: No such file or directory
arho@ohra-laptop:~/Asiakirjat/pymunk-0.1$ 
```
But what's wrong? :confused: Why it isn't already running?

---

### Post by loell on 2008-09-06
> ChipmunkPyEd.dll

could it be that this module is for windows only?

---

### Post by crazyfuturamanoob on 2008-09-06
Pymunk & chipmunk are windows only!??!?! Is there similar physics engine for ubuntu then?

[SIZE="1"]All good things are being made for the crap windows...[/SIZE]

---

### Post by Kadrus on 2008-09-06
No,its cross platform.
You need to download Chipmunk.([http://wiki.slembcke.net/main/published/Chipmunk](http://wiki.slembcke.net/main/published/Chipmunk))
and do: cmake(sudo apt-get install cmake)
and then you need to run the python installer from pymunk.
I believe it would be something **python setup.py**
and then things should work.

---

### Post by sallywon on 2008-09-06
I do it and my paython works. thank you!

---

### Post by crazyfuturamanoob on 2008-09-06
> **Kadrus said:**
> No,its cross platform.
You need to download Chipmunk.([http://wiki.slembcke.net/main/published/Chipmunk](http://wiki.slembcke.net/main/published/Chipmunk))
and do: cmake(sudo apt-get install cmake)
and then you need to run the python installer from pymunk.
I believe it would be something **python setup.py**
and then things should work.
I tried this, but it obviously doesn't work:
```
arho@ohra-laptop:~$ cd Chipmunk-4.0.2/
arho@ohra-laptop:~/Chipmunk-4.0.2$ cmake .
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
libglut requested but not found.
libGL requested but not found.
-- Configuring done
-- Generating done
-- Build files have been written to: /home/arho/Chipmunk-4.0.2
arho@ohra-laptop:~/Chipmunk-4.0.2$ make
Scanning dependencies of target chipmunk
[  2%] Building C object src/CMakeFiles/chipmunk.dir/chipmunk.o
[  5%] Building C object src/CMakeFiles/chipmunk.dir/cpArbiter.o
[  8%] Building C object src/CMakeFiles/chipmunk.dir/cpArray.o
[ 11%] Building C object src/CMakeFiles/chipmunk.dir/cpBB.o
[ 14%] Building C object src/CMakeFiles/chipmunk.dir/cpBody.o
[ 17%] Building C object src/CMakeFiles/chipmunk.dir/cpCollision.o
[ 20%] Building C object src/CMakeFiles/chipmunk.dir/cpHashSet.o
[ 23%] Building C object src/CMakeFiles/chipmunk.dir/cpJoint.o
[ 26%] Building C object src/CMakeFiles/chipmunk.dir/cpPolyShape.o
/home/arho/Chipmunk-4.0.2/src/cpPolyShape.c:127:2: warning: no newline at end of file
[ 29%] Building C object src/CMakeFiles/chipmunk.dir/cpShape.o
[ 32%] Building C object src/CMakeFiles/chipmunk.dir/cpSpace.o
[ 35%] Building C object src/CMakeFiles/chipmunk.dir/cpSpaceHash.o
[ 38%] Building C object src/CMakeFiles/chipmunk.dir/cpVect.o
Linking C shared library libchipmunk.so
[ 38%] Built target chipmunk
Scanning dependencies of target chipmunk_static
[ 41%] Building C object src/CMakeFiles/chipmunk_static.dir/chipmunk.o
[ 44%] Building C object src/CMakeFiles/chipmunk_static.dir/cpArbiter.o
[ 47%] Building C object src/CMakeFiles/chipmunk_static.dir/cpArray.o
[ 50%] Building C object src/CMakeFiles/chipmunk_static.dir/cpBB.o
[ 52%] Building C object src/CMakeFiles/chipmunk_static.dir/cpBody.o
[ 55%] Building C object src/CMakeFiles/chipmunk_static.dir/cpCollision.o
[ 58%] Building C object src/CMakeFiles/chipmunk_static.dir/cpHashSet.o
[ 61%] Building C object src/CMakeFiles/chipmunk_static.dir/cpJoint.o
[ 64%] Building C object src/CMakeFiles/chipmunk_static.dir/cpPolyShape.o
/home/arho/Chipmunk-4.0.2/src/cpPolyShape.c:127:2: warning: no newline at end of file
[ 67%] Building C object src/CMakeFiles/chipmunk_static.dir/cpShape.o
[ 70%] Building C object src/CMakeFiles/chipmunk_static.dir/cpSpace.o
[ 73%] Building C object src/CMakeFiles/chipmunk_static.dir/cpSpaceHash.o
[ 76%] Building C object src/CMakeFiles/chipmunk_static.dir/cpVect.o
Linking C static library libchipmunk_static.a
[ 76%] Built target chipmunk_static
Scanning dependencies of target ../../chipmunk_demos
[ 79%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo1.o
[ 82%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo2.o
[ 85%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo3.o
[ 88%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo4.o
[ 91%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo5.o
[ 94%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo6.o
[ 97%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/Demo7.o
[100%] Building C object Demo/CMakeFiles/../../chipmunk_demos.dir/main.o
/home/arho/Chipmunk-4.0.2/Demo/main.c:35:20: error: GL/gl.h: No such file or directory
/home/arho/Chipmunk-4.0.2/Demo/main.c:36:23: error: GL/glext.h: No such file or directory
/home/arho/Chipmunk-4.0.2/Demo/main.c:37:21: error: GL/glu.h: No such file or directory
/home/arho/Chipmunk-4.0.2/Demo/main.c:38:22: error: GL/glut.h: No such file or directory
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘drawCircle’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:123: warning: implicit declaration of function ‘glBegin’
/home/arho/Chipmunk-4.0.2/Demo/main.c:123: error: ‘GL_LINE_STRIP’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:123: error: (Each undeclared identifier is reported only once
/home/arho/Chipmunk-4.0.2/Demo/main.c:123: error: for each function it appears in.)
/home/arho/Chipmunk-4.0.2/Demo/main.c:126: warning: implicit declaration of function ‘glVertex2f’
/home/arho/Chipmunk-4.0.2/Demo/main.c:129: warning: implicit declaration of function ‘glEnd’
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘drawSegmentShape’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:147: error: ‘GL_LINES’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘drawPolyShape’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:161: error: ‘GL_LINE_LOOP’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘display’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:197: warning: implicit declaration of function ‘glClear’
/home/arho/Chipmunk-4.0.2/Demo/main.c:197: error: ‘GL_COLOR_BUFFER_BIT’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:199: warning: implicit declaration of function ‘glColor3f’
/home/arho/Chipmunk-4.0.2/Demo/main.c:206: error: ‘GL_POINTS’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:217: warning: implicit declaration of function ‘glutSwapBuffers’
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘timercall’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:238: warning: implicit declaration of function ‘glutTimerFunc’
/home/arho/Chipmunk-4.0.2/Demo/main.c:240: warning: implicit declaration of function ‘glutPostRedisplay’
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘initGL’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:250: warning: implicit declaration of function ‘glClearColor’
/home/arho/Chipmunk-4.0.2/Demo/main.c:252: warning: implicit declaration of function ‘glPointSize’
/home/arho/Chipmunk-4.0.2/Demo/main.c:254: warning: implicit declaration of function ‘glEnable’
/home/arho/Chipmunk-4.0.2/Demo/main.c:254: error: ‘GL_LINE_SMOOTH’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:255: error: ‘GL_POINT_SMOOTH’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:256: error: ‘GL_BLEND’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:257: warning: implicit declaration of function ‘glBlendFunc’
/home/arho/Chipmunk-4.0.2/Demo/main.c:257: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:257: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:258: warning: implicit declaration of function ‘glHint’
/home/arho/Chipmunk-4.0.2/Demo/main.c:258: error: ‘GL_LINE_SMOOTH_HINT’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:258: error: ‘GL_DONT_CARE’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:259: error: ‘GL_POINT_SMOOTH_HINT’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:260: warning: implicit declaration of function ‘glLineWidth’
/home/arho/Chipmunk-4.0.2/Demo/main.c:262: warning: implicit declaration of function ‘glMatrixMode’
/home/arho/Chipmunk-4.0.2/Demo/main.c:262: error: ‘GL_PROJECTION’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:263: warning: implicit declaration of function ‘glLoadIdentity’
/home/arho/Chipmunk-4.0.2/Demo/main.c:264: warning: implicit declaration of function ‘glOrtho’
/home/arho/Chipmunk-4.0.2/Demo/main.c:265: warning: implicit declaration of function ‘glTranslatef’
/home/arho/Chipmunk-4.0.2/Demo/main.c: In function ‘glutStuff’:
/home/arho/Chipmunk-4.0.2/Demo/main.c:270: warning: implicit declaration of function ‘glutInit’
/home/arho/Chipmunk-4.0.2/Demo/main.c:272: warning: implicit declaration of function ‘glutInitDisplayMode’
/home/arho/Chipmunk-4.0.2/Demo/main.c:272: error: ‘GLUT_DOUBLE’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:272: error: ‘GLUT_RGBA’ undeclared (first use in this function)
/home/arho/Chipmunk-4.0.2/Demo/main.c:274: warning: implicit declaration of function ‘glutInitWindowSize’
/home/arho/Chipmunk-4.0.2/Demo/main.c:275: warning: implicit declaration of function ‘glutCreateWindow’
/home/arho/Chipmunk-4.0.2/Demo/main.c:279: warning: implicit declaration of function ‘glutDisplayFunc’
/home/arho/Chipmunk-4.0.2/Demo/main.c:280: warning: implicit declaration of function ‘glutKeyboardFunc’
/home/arho/Chipmunk-4.0.2/Demo/main.c:286: warning: implicit declaration of function ‘glutMainLoop’
make[2]: *** [Demo/CMakeFiles/../../chipmunk_demos.dir/main.o] Virhe 1
make[1]: *** [Demo/CMakeFiles/../../chipmunk_demos.dir/all] Virhe 2
make: *** [all] Virhe 2
arho@ohra-laptop:~/Chipmunk-4.0.2$ python setup.py
python: can't open file 'setup.py': [Errno 2] No such file or directory
arho@ohra-laptop:~/Chipmunk-4.0.2$ 
```

---

### Post by Kadrus on 2008-09-06
the setup.py is in the pymunk directory,not the chipmunk.

---

### Post by crazyfuturamanoob on 2008-09-07
I can't find setup.py anywhere! So could I have a step-by-step instructions.
What should be the  working directory of each step, should I have pymunk folder inside chipmunk folder?

Or is there any other physics engine, that would be easier to install?

---

### Post by Kadrus on 2008-09-07
Download pymunk from  [http://pymunk.googlecode.com/files/pymunk-0.8.zip](http://pymunk.googlecode.com/files/pymunk-0.8.zip)
Extract and place it in your home dir.It comes with chipmunk.
cd into the directory : cd ~/pymunk-0.8
then go into the chipmunk dir: cd chipmunk_src
then compile:```
gcc -O3 -std=gnu99 -ffast-math -c *.c
```
After that go back to the pymonk dir:cd ../ and run: python setup.py install
This should work..

---

### Post by crazyfuturamanoob on 2008-09-07
> **Kadrus said:**
> Download pymunk from  [http://pymunk.googlecode.com/files/pymunk-0.8.zip](http://pymunk.googlecode.com/files/pymunk-0.8.zip)
Extract and place it in your home dir.It comes with chipmunk.
cd into the directory : cd ~/pymunk-0.8
then go into the chipmunk dir: cd chipmunk_src
then compile:```
gcc -O3 -std=gnu99 -ffast-math -c *.c
```
After that go back to the pymonk dir:cd ../ and run: python setup.py install
This should work..
Now what?
```

arho@ohra-laptop:~$ cd pymunk-0.8/chipmunk_src/
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ gcc -03 -std=gnu99 -ffast-math -c *.c
gcc: unrecognized option '-03'
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ 

```

---

### Post by Zugzwang on 2008-09-07
> **crazyfuturamanoob said:**
> Now what?
```

arho@ohra-laptop:~$ cd pymunk-0.8/chipmunk_src/
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ gcc -03 -std=gnu99 -ffast-math -c *.c
gcc: unrecognized option '-03'
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ 

```

It's "-O3", not "-03". Anyway, your compiling problems above (chipmunk) could be solved the following way.

Note that the first error message is that "GL/gl.h" was not found. So it might be the case that some package is missing. We use [http://packages.ubuntu.com](http://packages.ubuntu.com) to find a suitable package. So we search for a package containing "GL/gl.h" and we get a list:
[LIST]
[*]mingw32-runtime
[*]mesa-common-dev
[*]nvidia-glx-dev
[*]nvidia-glx-legacy-dev
[*]nvidia-glx-new-dev
[/LIST]
Since the first one is for Windows development and the last three are nvidia-only, try to install "mesa-common-dev" and you should be done!

---

### Post by crazyfuturamanoob on 2008-09-07
Ok, I managed to compile it, but can't run it because it doesn't find some files.
This is too hard, I can't make it. Is there another open-source python physics engine that I could use in my game and that is easier to install and use?

---

### Post by crazyfuturamanoob on 2008-09-10
Setup.py won't run:
```
arho@ohra-laptop:~[color=#19177C]$ [/color][color=#008000]cd [/color]Asiakirjat/pymunk-0.8/chipmunk_src/
arho@ohra-laptop:~/Asiakirjat/pymunk-0.8/chipmunk_src[color=#19177C]$ [/color]gcc -O3 -std[color=#666666]=[/color]gnu99 -ffast-math -c *.carho@ohra-laptop:~/Asiakirjat/pymunk-0.8/chipmunk_src[color=#19177C]$ [/color][color=#008000]cd[/color] ..
arho@ohra-laptop:~/Asiakirjat/pymunk-0.8[color=#19177C]$ [/color]python setup.py
usage: setup.py [color=#666666][[/color]global_opts[color=#666666]][/color] cmd1 [color=#666666][[/color]cmd1_opts[color=#666666]][/color] [color=#666666][[/color]cmd2 [color=#666666][[/color]cmd2_opts[color=#666666]][/color] ...[color=#666666]][/color]
   or: setup.py --help [color=#666666][[/color]cmd1 cmd2 ...[color=#666666]][/color]
   or: setup.py --help-commands
   or: setup.py cmd --help

error: no commands supplied
arho@ohra-laptop:~/Asiakirjat/pymunk-0.8[color=#19177C]$ [/color]

```

---

### Post by crazyfuturamanoob on 2008-09-29
So what I gotta type in terminal to make it working? What are the commands? Can't that setup just use the default commands?? HELP! Please, you gotta help me!

---

### Post by Wybiral on 2008-09-29
> **crazyfuturamanoob]Ok, I managed to compile it, but can't run it because it doesn't find some files.
This is too hard, I can't make it. Is there another open-source python physics engine that I could use in my game and that is easier to install and use?[/quote]

This is a VERY common task as a programmer (building libraries and dependencies)... Get used to it :)

[QUOTE=crazyfuturamanoob said:**
> Setup.py won't run:

Try "python setup.py install"

---

### Post by Kadrus on 2008-09-29
I beleive I gave you the instructions here :[http://ubuntuforums.org/showpost.php?p=5743220&postcount=8](http://ubuntuforums.org/showpost.php?p=5743220&postcount=8)
Read the documentation,if you are not willing to help yourself,no one will help you.

---

### Post by crazyfuturamanoob on 2008-09-29
> **Kadrus said:**
> I beleive I gave you the instructions here :[http://ubuntuforums.org/showpost.php?p=5743220&postcount=8](http://ubuntuforums.org/showpost.php?p=5743220&postcount=8)
Read the documentation,if you are not willing to help yourself,no one will help you.
I didn't notice that, sorry for bothering.

---

### Post by crazyfuturamanoob on 2008-09-29
Now I'm sure I got nothing to do with this weird problem.
```

arho@ohra-laptop:~$ cd pymunk-0.8/chipmunk_src/
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ gcc -O3 -std=gnu99 -ffast-math -c *.c
arho@ohra-laptop:~/pymunk-0.8/chipmunk_src$ cd ..
arho@ohra-laptop:~/pymunk-0.8$ python setup.py install
running install
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 13] Permission denied: '/usr/lib/python2.5/site-packages/test-easy-install-11223.write-test'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/lib/python2.5/site-packages/

Perhaps your account does not have write access to this directory?  If the
installation directory is a system-owned directory, you may need to sign in
as the administrator or "root" account.  If you do not have administrative
access to this machine, you may wish to choose a different installation
directory, preferably one that is listed in your PYTHONPATH environment
variable.

For information on other options, you may wish to consult the
documentation at:

  http://peak.telecommunity.com/EasyInstall.html

Please make the appropriate changes for your system and try again.

arho@ohra-laptop:~/pymunk-0.8$ 

```

Edit: Got it working with sudo.

---

### Post by Kadrus on 2008-09-29
If the problem is solved mark it in the thread.

---

### Post by crazyfuturamanoob on 2008-09-29
Ok, I will when it is solved.

But any of the examples in the example folder don't work. 

Here's the error message:
```

arho@ohra-laptop:~/pymunk-0.8/examples$ python box2d_pyramid.py 
Loading chipmunk for Linux (32bit) [/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/libchipmunk32.so]
Loading chipmunk for Linux (32bit) [/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/libchipmunk.so]
Traceback (most recent call last):
  File "box2d_pyramid.py", line 8, in <module>
    import pymunk
  File "/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/__init__.py", line 14, in <module>
    import _chipmunk as cp
  File "/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/_chipmunk.py", line 8, in <module>
    chipmunk_lib = load_library("chipmunk", print_path=_lib_debug)
  File "/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/libload.py", line 44, in load_library
    lib = ctypes.cdll.LoadLibrary(libfn)    
  File "/usr/lib/python2.5/ctypes/__init__.py", line 431, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python2.5/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk/libchipmunk.so: cannot open shared object file: No such file or directory
arho@ohra-laptop:~/pymunk-0.8/examples$ 

```

What's up? I got pymunk/chipmunk compiled.

---

### Post by crazyfuturamanoob on 2008-09-30
I finally figured out how to get it working. I had to rename "libchipmunk32.so" in
/usr/lib/python2.5/site-packages/pymunk-0.8-py2.5.egg/pymunk to "libchipmunk.so".
That solved the problem. Now I got pymunk working, and I can run the example files. 

WOW! 300+ bodies at the same time and no laag! This is awesome!
:guitar:

---

