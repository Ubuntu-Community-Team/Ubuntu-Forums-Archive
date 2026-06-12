---
title: "Want to start out with C++ / Game programming"
date: 2009-01-28
forum: Programming Talk
---

### Post by fastn on 2009-01-28
Hello, I'm very interested in starting out with C++ game development and learning more C++ from the ground. But I have no idea where to start or begin, or for that matter what tools is best to use and so on. I was wondering if anyone here got any tips for me about how to begin. Like what programs/websites or books I shall look into. I'm also interest in some Graphical C++ program(GUI) so any tips at that matter would be great.

At the moment I'm using Ubuntu 8.10 and know the basics in C++.

---

### Post by aj_ on 2009-01-28
Check out [http://www.gamedev.net/](http://www.gamedev.net/).

---

### Post by jimi_hendrix on 2009-01-28
[http://lazyfoo.net/SDL_tutorials/](http://lazyfoo.net/SDL_tutorials/)

if you can understand what hes doing in these, you can make some basic games

---

### Post by hessiess on 2009-01-28
GUI: use GTK/ QT/ WXwigits.

2D: Learn OpenGL unless you want your game to only run at a specific resolution, you could try out my Quad-Ren engine(which is based on OGL), which is resolution independent i.e. handles resolution/ scaling automatically. Though, as its fairly new there will still be some bugs that I haven't found yet.

3D: Eather learn OpenGL, Or use a 3D engine, which handles most of the complex math for you. Personally I recommend Irrlicht.

---

### Post by 42Wired on 2009-02-07
I'm doing the same. I've never compiled code in Ubuntu before, though, and I'm trying to compile Irrlicht from the source code using the command ```
make -f Makefile
```
(after changing to the directory containing the makefile), but I get output for what seems like every .cpp file that looks like ```
g++ -I../../include -Izlib -Ijpeglib -Ilibpng -DIRRLICHT_EXPORTS=1 -MM -MF CMS3DMeshFileLoader.d CMS3DMeshFileLoader.cpp
make: g++: Command not found
g++ -I../../include -Izlib -Ijpeglib -Ilibpng -DIRRLICHT_EXPORTS=1 -MM -MF CMD3MeshFileLoader.d CMD3MeshFileLoader.cpp
make: g++: Command not found
```
and ends in ```
g++ -Wall -pipe -g -D_DEBUG -I../../include -Izlib -Ijpeglib -Ilibpng -I/usr/X11R6/include -DIRRLICHT_EXPORTS=1  -c -o CBSPMeshFileLoader.o CBSPMeshFileLoader.cpp
make: g++: Command not found
make: *** [CBSPMeshFileLoader.o] Error 127

```
I've tried the readme and the -? option for the make command, but I still can't figure it out. Google seems to be of little help. Does anyone know what I'm doing wrong?

---

### Post by dribeas on 2009-02-07
Install build-essential and make sure that the g++ compiler is installed. Read the stickies, they do solve problems.

---

### Post by hessiess on 2009-02-07
Theres a tutorial here:

[http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux](http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux)

---

### Post by 42Wired on 2009-02-10
I got everything to compile. Thanks for everyone who helped. I didn't think to check the stickies, but I had been searching for so long on Google for how to do this I was too tired to read anything else...

However, I still have one more problem. I successfully compiled the first example, and it runs fine. The problem is that that is the only example program that will run. The others compile fine, but the executables don't appear to do anything.

---

