---
title: "Developing for Ubuntu?"
date: 2007-06-10
forum: Programming Talk
---

### Post by blah569 on 2007-06-10
I am thinking of installing Ubuntu on my laptop, and I am curious as if there is a IDE, SDK, etc for making Linux applications, or if there is not, how do you go about making a Linux application?  Please help.  Thanks.

---

### Post by Eric_Jardas on 2007-06-10
Not that I know of. But you don't need any special IDE, just use an editor and develop a program in your language and then create front end with a program like Glade.

---

### Post by blah569 on 2007-06-10
> **Eric_Jardas said:**
> Not that I know of. But you don't need any special IDE, just use an editor and develop a program in your language and then create front end with a program like Glade.


Thanks, but how do I get the Linux GUI?  Like, the buttons, etc.

---

### Post by Eric_Jardas on 2007-06-10
I already answered you:

> create front end with a program like Glade

:)

---

### Post by EndPerform on 2007-06-10
> **blah569 said:**
> Thanks, but how do I get the Linux GUI?  Like, the buttons, etc.

There's the GTK+ toolkit (Gnome) and then there's QT (KDE).  Those are the two major ones.  As Eric_Jardas mentioned, Glade can help you with GTK+ apps.

---

### Post by thelinuxguy on 2007-06-10
Java
[INDENT][http://www.linuxjournal.com/article/8111](http://www.linuxjournal.com/article/8111)[/INDENT]
PyGTK
[INDENT][http://www.pygtk.org/](http://www.pygtk.org/)[/INDENT]
Glade interface designer
[INDENT][http://glade.gnome.org/](http://glade.gnome.org/)[/INDENT]

Whole lot of other options as well. Depends on what you are comfortable with.

---

### Post by moma on 2007-06-10
[COLOR="Red"]A newer version of this posting is available here:[/COLOR] [http://ubuntuforums.org/showthread.php?p=3627418#post3627418]("http://ubuntuforums.org/showthread.php?p=3627418#post3627418") <---  Go there ;-)

--------------------------------------------------------
The old one:

The Code::Blocks IDE is a superb developer studio for C/C++ programming. See [http://codeblocks.org](http://codeblocks.org)

I recommend that you use the wxWidgets library for GUI programming. WxWidgets is excellent, portable and easy-to-learn GUI kit.  
Study: [http://www.wxwidgets.org/](http://www.wxwidgets.org/)

Code::Blocks itself is programmed with wxWidgets.

**This is howto install Code::Blocks IDE on Ubuntu Linux 7.04.**

Do this:
**[COLOR="Red"]0)[/COLOR]** First, install some necessities. Issue these commands on the command line. (do not write the $ sign. It just denotes the command prompt).

$ [COLOR="SeaGreen"]sudo apt-get install build-essential gdb subversion[/COLOR]

$ [COLOR="SeaGreen"]sudo apt-get install automake autoconf libtool[/COLOR]

$[COLOR="SeaGreen"] sudo apt-get install libgtk2.0-dev libxmu-dev libxxf86vm-dev  [/COLOR]

I recommend that you move straight to wWidgets version 2.8.  The wxWidgets 2.6 is already 'history'.
$ [COLOR="SeaGreen"]sudo apt-get install libwxbase2.8-dev libwxgtk2.8-dev wx2.8-doc wx2.8-examples wx2.8-headers wx2.8-i18n  libwxbase2.8-dbg[/COLOR]

$ [COLOR="SeaGreen"]sudo ldconfig[/COLOR]

Goto step 2 if you run Ubuntu 7.10 (Gutsy Gibbon).

If you run Ubuntu 6.10(Edgy) or 7.04(feisty)  then
> {
	**[COLOR="Red"]1)[/COLOR]** Upgrade wxWidgets to version 2.8.4.
	Ubuntu comes with outdated version (v2.8.1) of wxWidgets. wxWidgets 2.8.1 is not good enough. You must upgrade it to wxWidgets 2.8.4.
	v2.8.4 fixes also some annoying bugs.

	Add the following line into your /etc/apt/sources.list file.  This should work on both x86 32 bits and 64 bits systems.
	[QUOTE][COLOR="SeaGreen"]deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) feisty main[/COLOR]

	Eg. you can edit /etc/apt/sources.list file with nano, gedit or kate editors. I employ the gedit editor here:
	$ [COLOR="SeaGreen"]sudo gedit /etc/apt/sources.list [/COLOR]

	Replace the word "feisty" with "edgy" if you run Ubuntu 6.10. 
	Notice: The upcoming Ubuntu 7.10 (alias Gutsy Gibbon, to be relased in october 2007) comes with wxWidgets v2.8.4 out of the box.

	Save the file and run the commands (All packages are security signed with a key. This imports the repo key to your machine. Approved).
	$ [COLOR="SeaGreen"]wget [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc)[/COLOR]
	$ [COLOR="SeaGreen"]sudo apt-key add key.asc[/COLOR]

	$ [COLOR="SeaGreen"]sudo apt-get update[/COLOR]

	An alternative guide for step 1: The official guide on wxWidgets' site has also good instructions for Ubuntu 7.04
	See: [http://www.wxwidgets.org/downloads/#latest_stable]("http://www.wxwidgets.org/downloads/#latest_stable")    ...under the **Binaries** section.
[/QUOTE]};

**[COLOR="Red"]2)[/COLOR]** Start the Synaptic Package Manager and Install / Upgrade all wxWidgets (v2.8 ) packages you can find, or just issue these commands:

$ [COLOR="SeaGreen"]sudo apt-get update[/COLOR]
$ [COLOR="SeaGreen"]sudo apt-get dist-upgrade[/COLOR]

Then set wxWidgets v2.8 as the default version.  Enter a correct number.  I normally select "gtk2-unicode-release-2.8" version.
$[COLOR="SeaGreen"] sudo update-alternatives --config wx-config[/COLOR]

You can check this setting by running
$ [COLOR="SeaGreen"]wx-config --version --selected-config[/COLOR]

**[COLOR="Red"]3)[/COLOR]** The actual installation of Code::Blocks IDE.
**3a)** Browse to the [http://forums.codeblocks.org/index.php/board,20.0.html]("http://forums.codeblocks.org/index.php/board,20.0.html") site.

**3b)** Choose the most recent nightly build page (by date) and clik on the on the **tar.gz** file name for Ubuntu 7.04.  It is a compressed file that contains several 
ready-made **.deb packages** for Ubuntu 6.10 and 7.04. The file name looks like this: [COLOR="Purple"]"....._Ubuntu6.10+7.04_wx2.8.4.tar.gz"[/COLOR].  Click on that file name and it will take you to the download site. 

Note: Not all nightly builds produce a new tar.gz package for Ubuntu, so take the most recent tar.gz file (by date) you can find. That's ok.  

**3c)** Now start the actual download from the BerliOS's site by clicking on the download link. 

**3d)**  Open the tar.gz file in Ubuntu's Archive Manager as shown [in picture 3d....]("http://www.futuredesktop.org/tmp/codeblocks_picture3d.png")

**3e)** And unzip the files to an empty directory in your $HOME folder. If necessary, create a new, empty directory under your home or Desktop folder. See [picture 3e....]("http://www.futuredesktop.org/tmp/codeblocks_picture3e.png")

**3f)** Now start the command line terminal from the Applications -> Accessories -> Terminal menu in GNOME. (In KDE, start the **Konsole** application from the menu). 

And cd to your download folder.  An example:
$ [COLOR="SeaGreen"]cd $HOME/Desktop/download[/COLOR]

**3g)** And install the .deb files by issuing this command
$ [COLOR="SeaGreen"]sudo dpkg -i  *deb[/COLOR]

***Of course, you can install the .deb packages by clicking on them in the Nautilus or Konqueror file managers. And that's it !***


**[COLOR="Red"]4)[/COLOR]** Run & test it. Issue the command 
$ [COLOR="SeaGreen"]codeblocks [/COLOR]

At the first start, select [COLOR="SeaGreen"]"GNU GCC compiler[/COLOR]" from the list.

Where,in which directory the install script put the codeblocks executable?  
$ [COLOR="SeaGreen"]which codeblocks [/COLOR]

Create an icon and put it on the desktop or toolbar. Enjoy !
If you are lazy then run the following command to create a shortcut icon on your Desktop:
$ [COLOR="SeaGreen"]sudo ln -s /usr/share/applications/codeblocks.desktop  $HOME/Desktop[/COLOR]


Code::Blocks has several project wizards that makes it easy to start with GUI coding.
Try eg. the menu selection:  File -> New -> Project ->  wxWidgets project. Select wxWidgets version v2.8. Compile and run.

**[COLOR="Red"]5)[/COLOR]** Update your Code::Blocks frequently.
Download and install new, updated tar.gz file (= .deb packages) from [http://forums.codeblocks.orgl]("http://forums.codeblocks.org/index.php/board,20.0.html")  site, as you did in the step 3) above.


[SIZE="1"]And if the installment fails then take a look at [this guide,,,,]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")
[/SIZE]
**---------------------------------------------------------------------------------------------------------**

[COLOR="Red"]Important notes.[/COLOR]
[COLOR="DarkOrange"]Uns comentários importantes.[/COLOR]

**Note 1:**
If you want to develope OpenGL (glut) applications, install FreeGlut first :-)
$ [COLOR="SeaGreen"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]

An important tip: Say: [COLOR="Purple"]**/usr**[/COLOR] when it asks "Please, Select GLUT's location:" in the Code::Blocks' glut-wizard (project wizard).
Read also the Note 2 below.
------------------------------

**Note 2 !:**
If you want to develope GLFW applications, install GLFW first ( [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) )
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
--------------------------------------------------------------
**Note 4 **, <nothing so far>

--------------------------------------------------------------
**Note 5 **, Important GLUT / OpenGL guides: 
[Redbook.html]("http://www.polytech.unice.fr/~buffa/cours/synthese_image/DOCS/trant.sgi.com/opengl/examples/redbook/redbook.html")
( [Redbook....]("http://www.opengl.org/documentation/red_book/")   [ direct [link...]("http://www.glprogramming.com/red") ] )
[Bluebook.html ]("http://www.gamedev.net/reference/count.asp?LinkID=611")   [ direct [link...]("http://www.glprogramming.com/blue") ]
[http://www.opengl.org/code/category/C19/]("http://www.opengl.org/code/category/C19/")
[http://nehe.gamedev.net/]("http://nehe.gamedev.net/")
[http://ubuntuforums.org/showthread.php?t=333867#8](http://ubuntuforums.org/showthread.php?t=333867#8)   Especially good source of programming guides !
[http://www.gamedev.net](http://www.gamedev.net)   ( example: how to run the[ lessons...]("http://ubuntuforums.org/showthread.php?p=2868563#post2868563") )
[http://www.glprogramming.com](http://www.glprogramming.com)

OpenGL Font library
[http://homepages.paradise.net.nz/henryj/code/#FTGL]("http://homepages.paradise.net.nz/henryj/code/#FTGL")

[http://www.libsdl.org]("http://www.libsdl.org/")  Simple Direct Media Layer (Excellent 2D library. Has also OpenGL support )
[http://lazyfoo.net/SDL_tutorials/index.php]("http://lazyfoo.net/SDL_tutorials/index.php")
or try
[http://g2.sourceforge.net/](http://g2.sourceforge.net/)
---
GLUI = OpenGL based GUI library (buttons, edit boxes, list boxes etc...)
[http://glui.sourceforge.net/]("http://glui.sourceforge.net/")
--------------------------------------------------------------

**Note 6 **, wxWidgets examples ! 
WxWidgets examples are installed in  /usr/share/doc/wx2.6-examples/examples/  OR   /usr/share/doc/wx2.8-examples/examples/ directories.

Use the "unpack_examples.sh" script (in the same directory) to unpack the samples in to your $HOME directory.  
For example, run:
$ [COLOR="SeaGreen"]/usr/share/doc/wx2.8-examples/examples/unpack_examples.sh   $HOME/wxwidgets2.8[/COLOR]

And it will unpack & put the samples in to **$HOME/wxwidgets2.8/samples/** folder.  

You can compile and run the examples directly from the command line. 

As an example let's compile the /popup sample code.
$ [COLOR="SeaGreen"]cd $HOME/wxwidgets2.8/samples/popup/[/COLOR]

Compile the project. 
$ [COLOR="SeaGreen"]make [/COLOR]

Run it  
$ [COLOR="SeaGreen"]./popup [/COLOR]
[COLOR="SeaGreen"]**./**[/COLOR]  means the current directory. Yu must include it, otherwise the shell will not find the program, because by default, the current directory is NOT in the $PATH. 
$ echo $PATH

**Study and compile all the wxWidgets' examples.**
--------------------------------------------------------------

**Note 7 **, Other important programming resources:  [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)

--------------------------------------------------------------

**Note 8 **, Essential [manual pages...]("http://en.wikipedia.org/wiki/Manual_page_(Unix)") that we developers often forget to install and use.

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

$ man 7 pthreads
$ man 7 sem_overview

Use also whatis and apropos commands (eg. to reveal the section number)
$ whatis pthread_create

$ apropos pthread_create
$ apropos pthread
--------------------------------------------------------------

**Note 9 **, "How to become a real hacker" by Eric S. Raymond, updated 2007 version.
[http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html)
--------------------------------------------------------------

**Note 10 **, A tip for zooming text in Code::Blocks IDE.
Press [COLOR="Purple"]CNTR[/COLOR] +  NUMPAD [COLOR="Purple"]**+**[/COLOR] or NUMPAD [COLOR="Purple"]**-**[/COLOR] keys to zoom the text.
NUMPAD +/- are tangents on the numerical keypad.
--------------------------------------------------------------

**Note 11 **, 
Windows converts, read this: [http://ubuntuforums.org/showthread.php?t=554070]("http://ubuntuforums.org/showthread.php?t=554070")

---

### Post by Zootropo on 2007-06-10
Python + PyGTK is very, very, very popular right now.
If you choose this language I would recommend Glade for the creation of the user interface and Eclipse with the pydev plugin to write the code.

---

### Post by pmasiar on 2007-06-10
Linux apps are written in many different languages. Ubuntu (as Linux distro) integrates selected apps as written by upstream developers. 

For own development, Ubuntu strongly prefers Python.

Before you start your own project, I would *strongly* recommend joining some existing projects (any of interest to you) to learn the ropes first.

---

### Post by Paul820 on 2007-06-10
Thanks for the howto moma...thanks!! I am going to have to learn how to upgrade the wx thing that codeblocks relies on, but i have never found any decent instructions on how to do it until now. Worked first time. Thanks again. :p

---

### Post by notones on 2007-08-08
Hello,

moma thanks for your how to, what about compiling wx from the soruce.

i have complied 2.8.4 from soruce and "make install"  it. 
but  i don't think the ones under the "usr/local/lib" is active.(compiled ones)

Still the apt-get installed versions active under usr/lib , what should i do to tell ubuntu to use the ones i installed by "make install".

and if i try to uninstall that packages , then it wants to uninstall a lot of other package for dep. purposes and i don't want to uninstall all of them.

And did you ever use eclipse with wx , what were your comments about eclipse ?

thanx in advance

---

### Post by cstudent on 2007-08-09
> **Paul820 said:**
> Thanks for the howto moma...thanks!! I am going to have to learn how to upgrade the wx thing that codeblocks relies on, but i have never found any decent instructions on how to do it until now. Worked first time. Thanks again. :p

You should have looked here:
[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

---

### Post by NeillHog on 2007-08-12
The code::blocks instructions also worked for me.
Perfectly!
And the "afterwards" I read tht it was for C++ and not Python which is what I really wanted - Call me Homer "Duuuhhh"

Thanks anyway.

Neill

---

### Post by Note360 on 2007-08-12
wxpython is wx for python... Works like a charm abit hard to install unfortuantly..

---

### Post by Grellin on 2007-09-03
I've been following the instructions and up to the point of installing Code Blocks, everything has worked as advertised. The problem I am running into is the nightly build won't install on the system I use (64bit instead of 32)

Here is the error I get from the terminal:

> grellin@grellin-desktop:~/codeblocks$ sudo dpkg -i *deb
dpkg: error processing codeblocks_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing codeblocks-contrib_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing codeblocks-dev_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing libcodeblocks0_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing libwxsmithlib0_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing libwxsmithlib0-dev_1.0svn4418_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 codeblocks_1.0svn4418_i386.deb
 codeblocks-contrib_1.0svn4418_i386.deb
 codeblocks-dev_1.0svn4418_i386.deb
 libcodeblocks0_1.0svn4418_i386.deb
 libwxsmithlib0_1.0svn4418_i386.deb
 libwxsmithlib0-dev_1.0svn4418_i386.deb


So I guess my question would be, is there a 64 bit compatible version or does anyone know of something obvious I have done wrong? Thanks.

---

### Post by Paul820 on 2007-09-03
I have an old .deb package from october the 11th if you want it or you can check out the source from svn and build it yourself. I use kdesvn for doing that, saves having to hunt down the deb packages. Here is the address: svn://svn.berlios.de/codeblocks/trunk

Or you can go to the codeblocks website and download the nightly build from there, someone builds it for amd64: [http://forums.codeblocks.org/index.php?PHPSESSID=adcbb264ca7bbade484ad3f3b2919e29&board=20.0]("http://forums.codeblocks.org/index.php?PHPSESSID=adcbb264ca7bbade484ad3f3b2919e29&board=20.0")

---

### Post by Grellin on 2007-09-03
Thanks for the reply. I found a nightly build (4413) that has amd64 also.

---

### Post by Paul820 on 2007-09-03
I just realised i put october 11th, i meant july 11th LOL.  Glad you found one anyway.

---

