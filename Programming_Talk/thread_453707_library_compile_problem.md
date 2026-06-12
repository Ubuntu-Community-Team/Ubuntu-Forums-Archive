---
title: "library compile problem"
date: 2007-05-24
forum: Programming Talk
---

### Post by gelax on 2007-05-24
hi, i have a problem whit irrlicht in  xubuntu 7.04.


[email]gelax@peppez:~/Desktop/irrlicht-1.2/examples/01.Hell[/email]oWorld$ make
g++ main.cpp -o example -I"../../include" -I"/usr/X11R6/include" -L"/usr/X11R6/lib" -L"../../lib/Linux" -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [all] Error 1
[email]gelax@peppez:~/Desktop/irrlicht-1.2/examples/01.Hell[/email]oWorld$ 


i need GL library?..... i have installed all *GL* from synaptic.....

please help me....
(i use nvidia driver 9631)

thanks ;)

(sorry for my english :D)

---

### Post by amo-ej1 on 2007-05-25
GL being OpenGL ;-)

---

### Post by moma on 2007-05-25
Install freeglut3-dev.

$ [COLOR=SeaGreen]sudo apt-get install freeglut3  freeglut3-dev[/COLOR]

+ study **note 1) **here
[http://ubuntuforums.org/showthread.php?p=1962696#post1962696](http://ubuntuforums.org/showthread.php?p=1962696#post1962696)

Notice also that Linux (and most of the Unices) use the "[Mesa]("http://en.wikipedia.org/wiki/Mesa_3D")" library that is a free implementation of the [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") sesification.  When you install [FreeGLUT]("http://freeglut.sourceforge.net/") it will also pull out many Mesa libraries (dependencies).  GLUT is great because it lets you develope multiplattform (cross platform) OpenGL applications.

The above Code::Blocks link mensions many great easy to follow guides. Don't miss'em.
----------------------------------------------------------------------

[COLOR="Sienna"]Additional info to newbie readers:  

Notice the link command. It says 
L"/usr/X11R6/lib" -L"../../lib/Linux" -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11

Which means that it wants the following *dynamic* link libraries: libIrrlicht.so  libGL.so,  libGLU.so, libXxf86vm.so , libX11.so and libXext.so 
The libraries could also be *static* libraries. Static libs are baked (linked) into the program. They have file-ending .a,  such as libIrrlicht.a.
---

You can easily find out what package provides the required library by using the dpkg -S command. For example:
What package comes with libGLU.so ?

$ dpkg -S  libGLU.so 
libglu1-mesa-dev: /usr/lib/libGLU.so
libglu1-mesa: /usr/lib/libGLU.so.1

The answer is libglu1-mesa package.
---

What package owns the header file glut.h ?

$ dpkg -S glut.h
freeglut3-dev: /usr/include/GL/glut.h

The answer is freeglut3-dev package.

What other files does it (freeglut3-dev) provide and where the files go?
$ dpkg -L freeglut3-dev
...
...
----
Other helpful commands are:
$ apt-cache search  packagename
and
$ apt-cache show packagename

You can learn more about these commands in "Other guides and manuals" section of [this document...]("http://www.futuredesktop.org/") Follow the links (blue rabbit).
[/COLOR]

---

### Post by moma on 2007-05-25
<Deleted>
Duplicate post. How to remove this?

---

### Post by gelax on 2007-05-25
thanks for the answer but the lib  (freeglut3 and freeglut3-dev) already were installed ;)



another info:

gelax@peppez:/usr/lib$ libGL
libGLcore.so.1 libGL.la libGLU.so
libGLcore.so.1.0.9631 libGL.so.1 libGLU.so.1
libGLEW.so.1.3 libGL.so.1.0.9631 libGLU.so.1.3.060502
libGLEW.so.1.3.4 libGLU.a
gelax@peppez:/usr/lib$ libGL

;)

---

### Post by WW on 2007-05-25
What version of Ubuntu are you using? What architecture? 32 or 64 bit?

I downloaded irrlicht-1.3, and I was able to compile the example in 01.HelloWorld, but the command run by make does not look the same as yours:
```

~/install/irrlicht/irrlicht-1.3/examples/01.HelloWorld$ make
Makefile:29: Building...
g++ -I../../include -I/usr/X11R6/include -O3 -ffast-math main.cpp -o ../../bin/Linux/01.HelloWorld -L/usr/X11R6/lib -L../../lib/Linux -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
~/install/irrlicht/irrlicht-1.3/examples/01.HelloWorld$

```
I am using dapper (32bit intel).

---

### Post by gelax on 2007-05-26
i use xubuntu 6.10 updated in 7.04 ...
 
 P4 2.4 32 bit processor.....

;)

---

### Post by moma on 2007-05-26
This distro is normal Feisty 32 bits.

I have testet irrlicht-1.3 and only the following packages were required.  Reinstall them all  (use the --reinstall option).  Run: 

$ [COLOR="SeaGreen"]sudo apt-get install --reinstall -y freeglut3 freeglut3-dev  libxmu-dev  libxext-dev  libxxf86vm-dev[/COLOR]

Then cd into your source/Irrlicht directory and run "make".

$ [COLOR="SeaGreen"]cd  irrlicht-1.3/source/Irrlicht[/COLOR]
$ [COLOR="SeaGreen"]make [/COLOR]

Watch for errors. Warnings are ok.

It compiles some test applications and puts them (the executables) into bin/Linux/ directory. Test the examples.
$ [COLOR="SeaGreen"]cd irrlicht-1.3/bin/Linux[/COLOR]

Test the first one
$ [COLOR="SeaGreen"]./01.HelloWorld[/COLOR]

The other examples will show a tiny menu which from you must choose the rendering back-end (OpenGL, DirectX, Software Renderer, etc..)
If you have installed OpenGL support for your graphics card, then select option [COLOR="Purple"]c) OpenGL[/COLOR].  Otherwise select [COLOR="Purple"]d) Software Renderer[/COLOR].
------------------------------------

Notice: I have not installed hardware acceleration (OpenGL) support for my graphics card. I have Nvidia 6800 LE card and  I currently run with the default "nv" driver. However, it is possible to code and test Irrlich with this setup (uses software renderer).  But the software renderer is not very good and of course it is immensely slow.

$  glxinfo | grep -i rendering
direct rendering: [COLOR="Red"]No[/COLOR]
---------------------------------

You should absolutely install a proper driver for your graphic card. It will give real OpenGL support. That means your display becomes hardware accelerated with lighting speed.  More about this in **step 6)** in [this document...]("http://www.futuredesktop.org/")   
[COLOR="SeaGreen"]glxinfo | grep -i rendering[/COLOR] should then report "Yes"

---

### Post by gelax on 2007-05-26
> I have testet irrlicht-1.3 and only the following packages were required. Reinstall them all (use the --reinstall option). Run:

$ sudo apt-get install --reinstall -y freeglut3 freeglut3-dev libxmu-dev libxext-dev libxxf86vm-dev

Then cd into your source/Irrlicht directory and run "make".

$ cd irrlicht-1.3/source/Irrlicht
$ make

Watch for errors. Warnings are ok.

It compiles some test applications and put them (the executables) into bin/Linux/ directory. Test the examples.
$ cd irrlicht-1.3/bin/Linux

Test the first one
$ ./01.HelloWorld

it does not work :(
the same error 

[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ make
Makefile:29: Building...
g++ -I../../include -I/usr/X11R6/include -O3 -ffast-math main.cpp -o ../../bin/Linux/01.HelloWorld -L/usr/X11R6/lib -L../../lib/Linux -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [all_linux] Error 1
[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ 


gelax@peppez:~$ glxinfo | grep -i rendering
direct rendering: Yes
gelax@peppez:~$ 


i use nvidia driver 9631 installed by nvidia.bin not from ubuntu restricted drive manager ;)
i use compiz without problems....

;)

---

### Post by moma on 2007-05-26
Hard to say what's wrong. 

1) Update the file-database and Locate libGL.so 
$ [COLOR="SeaGreen"]sudo updatedb [/COLOR]

Locate libGL.so
$ [COLOR="SeaGreen"]locate libGL.so[/COLOR]

Show also what symbolic links there are and sizes of the DLLs
$ [COLOR="SeaGreen"]ls -l  /usr/lib/*GL*[/COLOR]

Add the location of libGL.so to the compile and link command. 

$ [COLOR="SeaGreen"]cd  irrlicht-1.3/examples/01.HelloWorld[/COLOR]

And run 
$ [COLOR="SeaGreen"]g++ -I../../include -I/usr/X11R6/include -O3 -ffast-math main.cpp -o ../../bin/Linux/01.HelloWorld -L/usr/X11R6/lib -L../../lib/Linux  **-L/usr/lib/**   -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11[/COLOR]

I added -L/usr/lib/ to the command. 
It should not be necessary because /usr/lib/ and /usr/local/lib/ [and their sub folders] are hard coded defaults. Linux [spesifically:  ldd, ldconfig and runtime lib loader] knows about them.

PS. Where are the gurus ?!  Help.

PS: [COLOR="Red"]OpenGL v3.0 in sight and nearing.[/COLOR]
[http://www.theinquirer.net/default.aspx?article=39846](http://www.theinquirer.net/default.aspx?article=39846)

---

### Post by gelax on 2007-05-27
> gelax@peppez:~$ locate libGL.so
/usr/lib/libGL.so.1
/usr/lib/libGL.so.1.0.9631
gelax@peppez:~$ 


> 
gelax@peppez:~$ ls -l /usr/lib/*GL*
lrwxrwxrwx 1 root root      21 2007-04-20 22:12 /usr/lib/libGLcore.so.1 -> libGLcore.so.1.0.9631
-rwxr-xr-x 1 root root 8961144 2007-04-20 22:12 /usr/lib/libGLcore.so.1.0.9631
lrwxrwxrwx 1 root root      16 2007-04-20 15:06 /usr/lib/libGLEW.so.1.3 -> libGLEW.so.1.3.4
-rw-r--r-- 1 root root  199848 2007-03-05 06:16 /usr/lib/libGLEW.so.1.3.4
-rw-r--r-- 1 root root     653 2007-04-20 22:12 /usr/lib/libGL.la
lrwxrwxrwx 1 root root      17 2007-04-20 22:12 /usr/lib/libGL.so.1 -> libGL.so.1.0.9631
-rwxr-xr-x 1 root root  567628 2007-04-20 22:12 /usr/lib/libGL.so.1.0.9631
-rw-r--r-- 1 root root  679976 2007-03-31 01:07 /usr/lib/libGLU.a
lrwxrwxrwx 1 root root      11 2007-04-20 15:06 /usr/lib/libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root      20 2007-04-20 15:06 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060502
-rw-r--r-- 1 root root  521000 2007-03-31 01:07 /usr/lib/libGLU.so.1.3.060502

/usr/lib/GLUT-2.0:
totale 4
drwxr-xr-x 4 root root 4096 2007-05-24 22:53 ghc-6.6

/usr/lib/OpenGL-2.1:
totale 4
drwxr-xr-x 4 root root 4096 2007-05-24 22:53 ghc-6.6
gelax@peppez:~$ 




> gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.HelloWorld$ g++ -I../../include -I/usr/X11R6/include -O3 -ffast-math main.cpp -o ../../bin/Linux/01.HelloWorld -L/usr/X11R6/lib -L../../lib/Linux -L/usr/lib/ -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11L/usr/X11R6/lib -L../../lib/Linux -L/usr/lib/ -lIrrlicht -lGL -lGLU/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ 


the same error :(

---

### Post by moma on 2007-05-27
Well, there is an error in your installation after all.

The following command will fix it:
$ [COLOR="SeaGreen"]sudo ln -s /usr/lib/libGL.so.1  /usr/lib/libGL.so[/COLOR]

[COLOR="Red"]EDIT:[/COLOR] Big fingers to blame: The statement had a syntax error. It's fixed now.

---

### Post by gelax on 2007-05-27
thanks! :D, (Now no GL error) but there are a different problem 

> gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.HelloWorld$ make
Makefile:29: Building...
g++ -I../../include -I/usr/X11R6/include -O3 -ffast-math main.cpp -o ../../bin/Linux/01.HelloWorld -L/usr/X11R6/lib -L../../lib/Linux -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ 


the make does not create any executable... :(

after make:
> 
[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ ls -l
totale 80
-rw-r--r-- 1 gelax root   878 2006-07-21 01:30 example.cbp
-rw-r--r-- 1 gelax root   991 2006-06-27 11:47 example.dev
-rw-r--r-- 1 gelax root  4363 2006-08-05 11:59 HelloWorld.dsp
-rw-r--r-- 1 gelax root   571 2006-08-05 11:59 HelloWorld.dsw
-rw-r--r-- 1 gelax root   909 2006-08-05 12:45 HelloWorld.sln
-rw-r--r-- 1 gelax root  5216 2007-02-07 23:26 HelloWorld_vc8.vcproj
-rw-r--r-- 1 gelax root  4456 2006-12-28 14:52 HelloWorld.vcproj
-rw-r--r-- 1 gelax root  8267 2007-03-11 16:35 main.cpp
-rw-r--r-- 1 gelax root  1160 2007-03-01 17:55 Makefile
-rw-r--r-- 1 gelax root 23687 2006-06-19 20:54 tutorial.html
[email]gelax@peppez:~/Desktop/irrlicht-1.3/irrlicht-1.3/examples/01.Hell[/email]oWorld$ 


---

### Post by moma on 2007-05-27
Yes it does. It builds the executable but you must walk after it.
Read this posting: [http://ubuntuforums.org/showthread.php?p=2723474#post2723474](http://ubuntuforums.org/showthread.php?p=2723474#post2723474)
The next green line after "make".

Also study the compilation command. It says that output (-o) is to
-o [COLOR="DarkOrchid"]**../../bin/Linux/**[/COLOR]01.HelloWorld

It's not bin/laden ;-)

Tell us how you do. ok?

---

### Post by gelax on 2007-05-27
lol :D

in the version that I used in mandriva it was different :D

now works very well :o

many thanks moma for the help! ;)

---

