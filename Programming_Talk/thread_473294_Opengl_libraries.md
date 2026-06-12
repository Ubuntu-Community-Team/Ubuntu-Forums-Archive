---
title: "Opengl libraries"
date: 2007-06-13
forum: Programming Talk
---

### Post by james_2002uk on 2007-06-13
Hi!

I recently decided to give programming in openGL a go. I've been having a look at some online tutorials and stuff. I compiled an example program and it did it with no errors but on building it says "Undefined reference to glfunction_name". I know I have to link the compiler to the libraries, but i don't know where to find them.

The tutorial I used said I would need "opengl32.lib", "glu32.lib" and "glut32.lib". 
Does anyone know where I can find these files, I've downloaded freeglut3, libglut3 and glutg3 so they may be on my system somewhere, i've had a look but don't really know where to find them (I've checked /usr/lib, /usr/include, /usr/local/lib, /usr/local/include etc)

Thanks allot!

Jim

---

### Post by dave_567 on 2007-06-14
I know where to find the files......

"opengl32.lib"   --->  c:\winnt\system32

"glu32.lib"   --->   c:\Program Files\Microsoft Visual Studio\VC98\Lib

"glut32.lib"   --->   c:\Program Files\Microsoft Visual Studio\VC98\Lib

Can you spot the problem?  ;-)


Install Mesa and I would suggest a different source page to work from.    

[http://www.mesa3d.org/](http://www.mesa3d.org/)

---

### Post by moma on 2007-06-15
Hello,
I recommend that you get Code::Blocks IDE. 
It has an OpenGL project wizard that makes it easy to start with OpenGL programming. GLUT (freeglut3) is portable OpenGL interface that manages mouse, keyboard, joystick and windows, on where you draw things.

Instructions are here: [http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)
After installation, read Note 1).
Note 5) has some important OpenGL guides.

You will also need a (opengl) driver for your graphic card.
Check step 6) [here...]("http://www.futuredesktop.org/")

Avoid installing from source. Start Synaptic Package Manager and check if it can offer a ready made package.

---

