---
title: "OpenGL, SDL, graphics, games"
date: 2007-06-18
forum: Programming Talk
---

### Post by Elisei on 2007-06-18
hi;

wondering if someone could tell me whats a good way to learn graphics programming on Linux, like OpenGL,  SDL and whatever else there is; i've got a few books for OpenGL but they are for windows, eventually it shouldn't matter of course but WinMain.cpp is not very Linux friendly;

thank for replies;

---

### Post by meatpan on 2007-06-18
MIT open courseware has a great introduction to computer graphics:

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-837Fall2003/CourseHome/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-837Fall2003/CourseHome/index.htm)

The class uses openGL.

---

### Post by moma on 2007-06-18
This forum has a good list of OpenGL resources and samples. Have you checked [http://ubuntuforums.org/showthread.php?t=333867#8]("http://ubuntuforums.org/showthread.php?t=333867#8") ?
Read also the [COLOR="red"]Note 5)[/COLOR] of [this page]("http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html").
GLUT library (packages freeglut3 and freeglut3-dev) makes OpenGL graphics programming very easy in Linux. OpenGL and glut are multiplatform libraries!
-----------------------------------------------------------------------------------------

How to run the lessons?

**Let's have an example:**
[COLOR="Red"]a)[/COLOR] Browse to  [http://nehe.gamedev.net](http://nehe.gamedev.net) website and move on to the  "**Lessons 01 - 05**" page.

[COLOR="Red"]b)[/COLOR] Then browse down to "**Your First Polygon:**" section and clik on the picture.  It will take you to the code.  
[http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02")
Read and study the explanation.

[COLOR="Red"]c)[/COLOR] Then scroll down to the _bottom of the page_ and click on the "**DOWNLOAD [COLOR="SeaGreen"][B]Linux**[/COLOR] Code For This Lesson. ( Conversion by Richard Campbell )[/B]" link.  It will download (most likely a GLUT based) code for Linux.  There is also a special "GLUT" link but it is a GLUT sample for Windows. The difference is not so big but take the "Linux" code instead.

[COLOR="Red"]d)[/COLOR] Create a "lesson2" directory,  untar and put the files there.  

[COLOR="Red"]e)[/COLOR] Start gnome-terminal (menu selection: Applications -> Accessories -> Terminal)  and cd into your lesson2 directory.
$[COLOR="SeaGreen"] cd lesson2[/COLOR]

[COLOR="Red"]f)[/COLOR] Compile the sample code
$ [COLOR="SeaGreen"]make [/COLOR]

[COLOR="Red"]g)[/COLOR] Run it.
$ [COLOR="SeaGreen"]./lesson2[/COLOR]
------------------------

Notice: The above example requires GLUT Library (in Linux: [freeglut3-dev]("http://freeglut.sourceforge.net/") package) and OpenGL (which in Linux is the [mesa]("http://www.mesa3d.org/") packages).  
Use the Synaptic Package Manager or run the following command on the command line and install freeglut3 and freeglut3-dev packages. All necessary packages are in your distro's package well (=repository).

$ [COLOR="SeaGreen"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]

Other important packages
$ sudo apt-get install build-essential gdb subversion
$ sudo apt-get install automake autoconf libtool
$ sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev

---

### Post by vexorian on 2007-06-18
Lovely link, thanks.

---

### Post by maddog39 on 2007-06-19
Here's a very very good beginning game programming tutorial series linked to on the libsdl.org website. Keep in mind though that SDL is 2D only but intergrates with OpenGL very well if you want to use them interchangably.  But SDL tends to be much much easier to learn in understand. So heres the link, check it out:

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

---

