---
title: "IDE OpenGL"
date: 2007-10-25
forum: Programming Talk
---

### Post by zergling on 2007-10-25
Hi everyone,
I open this Thread because I would like to learn the OpenGl, but I do not know where and which IDE I should use :(
Can someone help me please?
Bye and Thanks

---

### Post by Wybiral on 2007-10-25
With OpenGL it doesn't matter what IDE you use. What language are you planning to use?

---

### Post by zergling on 2007-10-25
Hi,
I am going to use C++

Could you tell me also what packages should I install to work with opengl please?
Bye and thx :)

---

### Post by moma on 2007-10-25
**The latest version is here**
[http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html)

-------------------------------------------------------------------------------------------------------------------------------------

[FONT="Arial Black"][SIZE="4"]Installation of Code::Blocks C/C++ IDE on ubuntu 8.04 (Hardy Heron):[/SIZE][/FONT]
See: [http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

[[img]http://bildr.no/thumb/166985.jpeg[/img]](http://bildr.no/view/166985)      Pictures:   [[img]http://bildr.no/thumb/166474.jpeg[/img]](http://bildr.no/view/166474)  

-------------------------------------------------------------------------------------------------------------------------------------

[FONT="Arial Black"][SIZE="4"]Installation of Code::Blocks C/C++ IDE on ubuntu 7.10 (Gutsy):[/SIZE][/FONT]
[http://www.codeblocks.org/]("http://www.codeblocks.org/")   [[img]http://bildr.no/thumb/115900.jpeg[/img]](http://bildr.no/view/115900)

[[img]http://bildr.no/thumb/115897.jpeg[/img]](http://bildr.no/view/115897)

LGP provides fresh Ubuntu-packages for codeblocks. See: [http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)
and [http://lgp203.free.fr/spip/spip.php?article1#nb2](http://lgp203.free.fr/spip/spip.php?article1#nb2)

You need to edit your /etc/apt/sources.list file and add the following repository lines there.
$ [COLOR="SeaGreen"]sudo gedit /etc/apt/sources.list [/COLOR]
```
## Repository for codeblocks IDE and wxWidgets 2.8.6 
## Note: from revision 4592, the nightly builds will depend/based upon wxWidgets 2.8.6.
deb http://lgp203.free.fr/ubuntu/ gutsy  universe
deb http://apt.wxwidgets.org/ gutsy-wx main
```

Add these security keys to your package system  (the packages are signed with these keys). Run the commands
$ [COLOR=SeaGreen]wget -q [http://lgp203.free.fr/public.key](http://lgp203.free.fr/public.key) -O- | sudo apt-key add -[/COLOR]
$ [COLOR=SeaGreen]wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -[/COLOR]


Then install 
$ [COLOR="SeaGreen"]sudo apt-get update [/COLOR]
$[COLOR="SeaGreen"] sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib[/COLOR]

For code development, you'll also need some additional packages. Install 
$ [COLOR="SeaGreen"]sudo apt-get install build-essential gdb subversion[/COLOR]

$ [COLOR="SeaGreen"]sudo apt-get install automake autoconf libtool[/COLOR]

$[COLOR="SeaGreen"] sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev  [/COLOR]

These package are for programming with the wxWidgets GUI toolkit.
$[COLOR="SeaGreen"] sudo apt-get install libwxbase2.8-dev wx2.8-headers libwxgtk2.8-dev[/COLOR]
-------------------

Then start the codeblocks IDE from the menu or CLI:
$ [COLOR="SeaGreen"]codeblocks[/COLOR]

-------------------
Below are some important notes. Especially read notes 1-  5.   
Use the (glut) **freeglut** library to develope portable OpenGL applications.  
Code::Blocks has a **GLUT project wizard**.  Use it to create your first OpenGL project. Build & run.

-------------------

[COLOR="Red"]Important notes.[/COLOR]
[COLOR="DarkOrange"]Alguns comentários importantes.[/COLOR]

**Note 1:**
If you want to develope OpenGL ([glut...]("http://freeglut.sourceforge.net/")) applications, install FreeGlut first :-)  Type
$ [COLOR="SeaGreen"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]

Select "GLUT project" in the codeblocks' project wizard.
An important tip: Say: [COLOR="Purple"]**/usr**[/COLOR] when it asks "Please, Select GLUT's location:".  
See picture [[img]http://bildr.no/thumb/167023.jpeg[/img]](http://bildr.no/view/167023)
Read also the Note 5) below.
------------------------------

**Note 2 !:**
If you want to develope GLFW applications, install GLFW first ( [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) )
Read also this [posting...]("http://ubuntuforums.org/showthread.php?p=3630703#post3630703")
------------------------------

**Note 3 **, c-cpp-reference:
Do not forget to install the "c-cpp-reference" manuals.  Run this command:
$ [COLOR="SeaGreen"]sudo apt-get install c-cpp-reference[/COLOR]

OR use your Synaptic Package Manager and get the package. It will put some HTML help files in the  /usr/share/doc/c-cpp-reference/ directory. 
Start Firefox and point it to **/usr/share/doc/c-cpp-reference/index.html**

Also these web C/C++ sites are very helpful:
[http://www.cppreference.com/](http://www.cppreference.com/)
+
[http://www.cplusplus.com]("http://www.cplusplus.com/")
+
[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html) 

+ The ultimate collection of C++ tutorials
[http://ubuntuforums.org/showthread.php?t=333867#2](http://ubuntuforums.org/showthread.php?t=333867#2)  and [C++ wikibook...]("http://en.wikibooks.org/wiki/C%2B%2B")
+ STL (Standard Template Library) guide
[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html)   (simple samples [test-std1.cpp]("http://www.futuredesktop.org/tmp/test-std1.cpp")   and [test-std2.cpp]("http://www.futuredesktop.org/tmp/test-std2.cpp") ) 
--------------------------------------------------------------
**Note 4 **, <nothing so far>

--------------------------------------------------------------
**Note 5 **, Important GLUT / OpenGL guides: 
Read note 1) first, then study
[Redbook.html]("http://www.polytech.unice.fr/~buffa/cours/synthese_image/DOCS/trant.sgi.com/opengl/examples/redbook/redbook.html")
( [Redbook....]("http://www.opengl.org/documentation/red_book/")   [ direct [link...]("http://www.glprogramming.com/red") ] )
[Bluebook.html ]("http://www.gamedev.net/reference/count.asp?LinkID=611")   [ direct [link...]("http://www.glprogramming.com/blue") ]
[http://www.opengl.org/code/category/C19/]("http://www.opengl.org/code/category/C19/")
[http://nehe.gamedev.net/]("http://nehe.gamedev.net/")
[http://ubuntuforums.org/showthread.php?t=333867#8](http://ubuntuforums.org/showthread.php?t=333867#8)   Especially good source of programming guides !
[http://www.gamedev.net](http://www.gamedev.net)   ( example: how to run the[ lessons...]("http://ubuntuforums.org/showthread.php?p=2868563#post2868563") )
[http://www.glprogramming.com](http://www.glprogramming.com)
[http://ubuntu-gamedev.wikispaces.com]("http://ubuntu-gamedev.wikispaces.com/")  ( Ubuntu games )
[http://www.glchronicles.mccolm.org](http://www.glchronicles.mccolm.org) (GL Chronicles)

[http://www.libsdl.org]("http://www.libsdl.org/")  Simple Direct Media Layer (Excellent 2D library. Has also OpenGL support )
[http://lazyfoo.net/SDL_tutorials/index.php]("http://lazyfoo.net/SDL_tutorials/index.php")
or try
[http://g2.sourceforge.net/](http://g2.sourceforge.net/)
---
GLUI = OpenGL based GUI library (buttons, edit boxes, list boxes etc...)
[http://glui.sourceforge.net/]("http://glui.sourceforge.net/")

FTGL = Render text (fonts) in OpenGL
[http://homepages.paradise.net.nz/henryj/code/#FTGL]("http://homepages.paradise.net.nz/henryj/code/#FTGL")

Animated OpenGL graphical UI
[http://clutter-project.org](http://clutter-project.org)  (Clutter)
[https://code.fluendo.com/pigment/trac](https://code.fluendo.com/pigment/trac)  (and Pigment)

OpenAL sound
[http://www.openal.org](http://www.openal.org)

Ubuntu gamers' corner
[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)
--------------------------------------------------------------

**Note 6 **, wxWidgets examples ! 
WxWidgets is a multi platform GUI toolkit: [http://www.wxwidgets.org]("http://www.wxwidgets.org/")

First, get the package wx2.8-examples
$ [COLOR="SeaGreen"]sudo apt-get install wx2.8-examples[/COLOR]

The package puts the examples into **/usr/share/doc/wx2.8-examples/examples/** directory. It's a compressed tar-ball which you have to unpack/untar.
( If you have the older 2.6 version then the directory is /usr/share/doc/wx2.6-examples/examples/  )

Run the "unpack_examples.sh" script (in the same directory) to unpack the samples in to your $HOME directory.  
For example, run:
$ [COLOR="SeaGreen"]/usr/share/doc/wx2.8-examples/examples/unpack_examples.sh   $HOME/wxwidgets2.8[/COLOR]

And it will unpack & put the samples in to **$HOME/wxwidgets2.8/samples/** folder.  

You can compile and run the examples directly from the command line. 
The compilaton requires wxWidgets' development headers and libraries. **You will need packages:** [COLOR="DimGray"]libwxbase2.8-dev  wx2.8-headers  libwxgtk2.8-dev[/COLOR]

As an example let's compile the /popup sample code.
$ [COLOR="SeaGreen"]cd $HOME/wxwidgets2.8/samples/popup/[/COLOR]

Compile the project. 
$ [COLOR="SeaGreen"]make [/COLOR]

Run it  
$ [COLOR="SeaGreen"]./popup [/COLOR]
[COLOR="SeaGreen"]**./**[/COLOR]  means the current directory. Yu must include it, otherwise the shell will not find the program, because by default, the current directory is NOT in the $PATH. 
$ echo $PATH

**Now, try to compile and run the other wxWidgets examples as well.**

Study also the wxWidgets' documentation package wx2.8-doc.
$ [COLOR="SeaGreen"]apt-cache search wx2.8-doc[/COLOR]
wx2.8-doc - wxWidgets Cross-platform C++ GUI toolkit (documentation)

Install it and list the documentation (html) files
$ [COLOR="SeaGreen"]dpkg -L wx2.8-doc[/COLOR]
$ [COLOR="DarkGreen"]dpkg -L wx2.8-doc | grep index[/COLOR]

Of course, the [documentation is available online too...]("http://www.wxwidgets.org/docs/")

+ read [http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)
and [http://en.wikibooks.org/wiki/WxWidgets](http://en.wikibooks.org/wiki/WxWidgets)
--------------------------------------------------------------

**Note 7 **, Necessary packages to develope SDL-applications.
SDL stands for [Simple DirectMedia Layer...]("http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer") 
It's a framework to greate portable 2D graphics applications. It also supports OpenGL.

First, list all packages that belong to the SDL family.
$ [COLOR="SeaGreen"]apt-cache search libsdl | grep dev[/COLOR]
The "-dev" packages contain the header (include) files and dynamic libraries for app development. You'll need them.

Install at least these basic packages. These give you a good start.
$ [COLOR="SeaGreen"]sudo aptitude install libsdl1.2-dev   libsdl-image1.2-dev   libsdl-sound1.2-dev  libsdl-mixer1.2-dev [/COLOR]
However, the most basic apps need only "libsdl1.2-dev".

Then create a basic SDL-application via the Code::Blocks' project wizard (select SDL project).
[[img]http://bildr.no/thumb/139790.jpeg[/img]](http://bildr.no/view/139790)

Other 2D/3D [frameworks...]("http://ubuntuforums.org/showthread.php?p=3635764#post3635764")
--------------------------------------------------------------

**Note 8 **, Make beautiful graphics with the Cairo
[http://cairographics.org/samples/](http://cairographics.org/samples/)  Cairo graphics !

MacSlow&#8217;s Cairo-Clock (a good example)
[http://macslow.thepimp.net/?page_id=23](http://macslow.thepimp.net/?page_id=23)
--------------------------------------------------------------

**Note 9 **, Other important programming resources:  [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)
Kernel, driver and module programmer's heaven: [http://www.futuredesktop.org/kernel.html](http://www.futuredesktop.org/kernel.html)

--------------------------------------------------------------

**Note 10 **, Essential [manual pages...]("http://en.wikipedia.org/wiki/Manual_page_(Unix)") that we developers often forget to install and use.

What manual pages does Ubuntu (or any other distro) offer?
$ [COLOR="SeaGreen"]apt-cache search manpages[/COLOR]
...
manpages - Manual pages about using a GNU/Linux system
**manpages-dev** - Manual pages about using GNU/Linux for development
manpages-posix - Manual pages about using POSIX system
**manpages-posix-dev** - Manual pages about using a POSIX system for development

Install all manpages*dev packages 
$ [COLOR="SeaGreen"]sudo apt-get install manpages-dev manpages-posix-dev[/COLOR]

Note:  This command vill tell you what manual sections (1 - 8 ) the package covers.
$ [COLOR="SeaGreen"]apt-cache show manpages-posix-dev[/COLOR]

Now search help: 
$ man 3 fprintf 
$ man sqrt 
$ man pthread_create
$ man sem_init

$ man 3 socket
$ man 7 pthreads
$ man 7 sem_overview

Use also whatis and apropos commands (eg. to reveal the section number)
$ whatis pthread_create

$ apropos pthread_create
$ apropos pthread
--------------------------------------------------------------

**Note 11 **, "How to become a real hacker" by Eric S. Raymond, updated 2007 version.
[http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html)
--------------------------------------------------------------

**Note 12 **, A tip for zooming text in Code::Blocks IDE.
Press [COLOR="Purple"]CNTR[/COLOR] +  NUMPAD [COLOR="Purple"]**+**[/COLOR] or NUMPAD [COLOR="Purple"]**-**[/COLOR] keys to zoom the text.
NUMPAD +/- are tangents on the numerical keypad.
--------------------------------------------------------------

**Note 13 **, Linux, speak to me.  Make your machine talk. YES TALK !
[http://ubuntuforums.org/showthread.php?t=291919](http://ubuntuforums.org/showthread.php?t=291919)
--------------------------------------------------------------

**Note 14** 77 useful Linux commands.
[http://searchenterpriselinux.techtarget.com/generic/0,295582,sid39_gci1282259,00.html](http://searchenterpriselinux.techtarget.com/generic/0,295582,sid39_gci1282259,00.html)
--------------------------------------------------------------

**Note 15 **, 
Windows converts, read this: [http://ubuntuforums.org/showthread.php?t=554070]("http://ubuntuforums.org/showthread.php?t=554070")

All users, read this: [http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)

---

### Post by Wybiral on 2007-10-25
> **zergling said:**
> Hi,
I am going to use C++

Could you tell me also what packages should I install to work with opengl please?
Bye and thx :)

SDL is a pretty good option for using OpenGL with C++, this will install OpenGL and SDL:
```

sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev libsdl1.2-dev

```

That's all you'll need to build SDL+OpenGL applications. SDL also has a bunch of additional libraries for things like image loading, text rendering, networking, audio, etc. It's also really portable and commonly used.

---

### Post by zergling on 2007-10-25
Hi guys, I would like to ask you something:
What is the difference between opengl, glut and glfw?
Is glut in c++ and gflw in c? What about just opengl?

I installed the glfw but I do not know what to put when the codeblock ask me Please select a GLFW's location.... 

Thx a lot both of you :) I REALLY appreciated your help !

P.S. May I start porgramming in OpenGL after covering just the basics of C++ such as loops, functions and array?
Or, do I need more C++?

---

### Post by moma on 2007-10-25
Re-hello,

From the [http://freeglut.sourceforge.net]("http://freeglut.sourceforge.net") web page:
> GLUT (and hence freeglut) framework let you Create and manage Windows containing OpenGL contexts on a wide range of platforms and also Read the mouse, Handle keyboard and joystick functions transparently.

So with freeglut, you can port your code  to several platforms (Linux, Unix, Windows, Mac) and be sure that Keyboard, Mouse and the basic Window functions  just work.  But OpenGL is OpenGL no matter you use it from freeglut or from other frameworks. OpenGL is OpenGL and need to be learned.
----------------

Ref. your GLFW question.  
**This is howto install GLFW** (it's not in the Ubuntu's package system).

$[COLOR="SeaGreen"] wget [http://prdownloads.sourceforge.net/glfw/glfw-2.6.tar.bz2](http://prdownloads.sourceforge.net/glfw/glfw-2.6.tar.bz2)[/COLOR]
$[COLOR="SeaGreen"] tar -xvjf glfw-2.6.tar.bz2 [/COLOR]
$ [COLOR="SeaGreen"]cd glfw[/COLOR]
 
$ [COLOR="SeaGreen"]make x11[/COLOR]

$ [COLOR="SeaGreen"]PREFIX=/usr sudo make x11-install[/COLOR]

$ [COLOR="SeaGreen"]sudo ldconfig[/COLOR]
--------

in the Code::Blocks GLFW's project wizard, say **[COLOR="Red"]/usr[/COLOR]** when it asks GLFW's location.
Because libraries inhabit the [COLOR="Red"]/usr/lib[/COLOR] directory and include files are in [COLOR="Red"]/usr/include/[/COLOR].


[COLOR="Red"]EDIT:[/COLOR]
The example code that is generated by the GLFW's project wizard needs also link to "libxrandr.so" library.
It means that you must install the libxrandr-dev package. 
$ [COLOR="SeaGreen"]sudo apt-get install libxrandr-dev[/COLOR]

And in Code::Blocks, use the wizard to create the sample code, browse to the menu selection **Project -> Build options....** and set the library under "Other link options"
See picture: [[img]http://bildr.no/thumb/115696.jpeg[/img]](http://bildr.no/view/115696)
--------

I recomend that you choose freeglut over GLFW because freeglut is more common, well known and tested library. Also supported by Ubuntu.
Both frameworks work well from C and C++.

---

### Post by moma on 2007-10-25
Duplicate posting. How to delete this?

---

### Post by hecato on 2007-10-25
mmm, I remember that was on edit advanced... "Edit your post, then there is a option for delete it" but I not see it now.... perhaps no longer available... or I'm remembering another board.

But should be enough if you only write "duplicate posting", like you do it.

---

### Post by Wybiral on 2007-10-25
GLUT is similar to SDL in that they are both portable abstraction layers. They allow you to get a window up with OpenGL, without having to deal with the lower-level GUI code (making it more portable because the same code works on a variety of systems).

I will note that GLUT is more of a prototyping tool and will impose some restrictions on how you construct your program (it forces program flow to be managed by it). SDL has more features geared towards games and more extensive OpenGL programs (such as cross platform multi-threading and thread-safe event/message handling), and gives you more freedom over the design.

---

### Post by zergling on 2007-10-25
Ok, if you say that freeglut is the best choise, I trust you :)
Thx thx so much my friends, I do Really appreciated all your help.
Grazie Mille :)

---

### Post by moma on 2007-10-26
Sounds good.
[COLOR="Red"]Learn to program OpenGL with the freeglut framework.[/COLOR]

Later, when you create bigger OpenGL applications (like SecondLife and similar ;-), then move to [COLOR="Green"] **[Panda 3D...]("http://www.panda3d.org/")**, **[Allegro...]("http://en.wikipedia.org/wiki/Allegro_library")**[/COLOR], [COLOR="DeepSkyBlue"]**[SDL...]("http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer")**[/COLOR], [COLOR="Purple"]**[Irrlicht...]("http://en.wikipedia.org/wiki/Irrlicht_Engine")**[/COLOR], [COLOR="Orange"]**[Ogre 3D...]("http://en.wikipedia.org/wiki/OGRE_3D")**[/COLOR] or  [OSG...]("http://www.openscenegraph.org")

EDIT: [Compile panda3d on Ubuntu 8.04...]("http://ubuntuforums.org/showthread.php?p=5522260#post5522260") (test)

Go back [to...]("http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html")

---

### Post by godvalve on 2007-11-13
OMG moma, I've never seen such a complete set of instructions on how to install / setup OpenGL on ubuntu before. I hope you don't mind, but I am going to reproduce these instructions on my website for other people needing this kind of help. [http://www.glchronicles.mccolm.org](http://www.glchronicles.mccolm.org)

---

### Post by slavik on 2007-11-13
> **zergling said:**
> Hi guys, I would like to ask you something:
What is the difference between opengl, glut and glfw?
Is glut in c++ and gflw in c? What about just opengl?

I installed the glfw but I do not know what to put when the codeblock ask me Please select a GLFW's location.... 

Thx a lot both of you :) I REALLY appreciated your help !

P.S. May I start porgramming in OpenGL after covering just the basics of C++ such as loops, functions and array?
Or, do I need more C++?
It should be enough.

You might want to learn about various data structures (stack, list, queue) since it would help you organize your data.

You might want to also read about and understand what a state machine is, since that is how OpenGL is organized.

---

### Post by Amablue on 2007-11-13
I'm trying to install the stuff Moma mentioned but I'm getting this error:

```
alex@ubuntu:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.6) but 2.8.4.0-0ubuntu3 is to be installed
E: Broken packages

```

I've already got libwxgtk2.8-0 installed, so I don't know what it's complaining about.

---

### Post by slavik on 2007-11-13
read the error carefully:

 libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.6) but 2.8.4.0-0ubuntu3 is to be installed

libwxgtk2.8-0 is not new enough ...

---

### Post by Amablue on 2007-11-13
What should I be installing then?

---

### Post by n00bgraphicsprogrammer on 2008-05-10
Hi, I just followed the Hardy Heron steps for installing Code::Blocks, freeglut, and wxwidgets.  I tried compiling the sample and everything runs fine except for one small but annoying problem:  The GLUT window is missing the title bar.  It is actually there but it just doesn't show it meaning I can click a non-existant "x" and it will close the window.  I tried compiling it using Code::Blocks and gcc using -lglut if that helps.  Both do the same thing.  Comparing what I see on my screen and the posted screenshot, the difference is the title bar obviously and the fact that I have a terminal type thing running which is what I think is wrong.  Any help would be appreciated.  Thanks in advance.

Sorry for the long post.

---

### Post by fabianmejia on 2008-10-01
I also suggest Code::Blocks, it's a great IDE and includes project wizards for Opengl, GLUT and SDL.

Please check a small howto:

[fabianmejia.blogspot.com]("http://fabianmejia.blogspot.com")

---

### Post by paladin_knight on 2010-11-02
I have installed the freeglut but when I started to build the glut project. I got the following error:

cannot find -lXxf86vm

---

### Post by slavik on 2010-11-02
Dead threads, stay dead.

---

