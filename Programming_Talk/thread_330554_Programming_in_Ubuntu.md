---
title: "Programming in Ubuntu"
date: 2007-01-03
forum: Programming Talk
---

### Post by suki on 2007-01-03
What compiling softwares do you use in Ubuntu to program in the following languages: c, c++, java, pc assembly, mips? Any other suggestions?

To get gcc, g++:
sudo apt-get install build-essential

Moved to Programming Talk forum.

---

### Post by taurus on 2007-01-03
Move over to Programming Talk.

---

### Post by meng on 2007-01-03
gcc is one of the staples here.

---

### Post by maxamillion on 2007-01-03
Language : Compiler/Emulator

C: gcc
C++: g++
Java: javac, gcj, jikes, eclipse(yes, eclipse has its own compiler)
x86 assembly: libASM, asm-toys
MIPS Assembly: [http://www.linux-mips.org/wiki/Emulators](http://www.linux-mips.org/wiki/Emulators)

---

### Post by suki on 2007-01-03
> **maxamillion said:**
> Language : Compiler/Emulator

C: gcc
C++: g++
Java: javac, gcj, jikes, eclipse(yes, eclipse has its own compiler)
x86 assembly: libASM, asm-toys
MIPS Assembly: [http://www.linux-mips.org/wiki/Emulators](http://www.linux-mips.org/wiki/Emulators)

Do you happen to know if there will be a graphical pop up if needed for javac? If so does it take a while?

---

### Post by Tomosaur on 2007-01-03
Javac is a command line utility, you compile stuff like this:

```

javac myFile.java

```

or ```

javac *.java

```
to compile all .java files in the current directory. It's generally pretty fast unless your processor is slow. There's no graphical popup.

---

### Post by pmasiar on 2007-01-03
Suki,

Excuse me if I am wrong, but it looks like you are beginnig programmer. We had a [poll ]("http://ubuntuforums.org/showthread.php?t=233405")recently, in opinion of many python is best language for a beginner. Less pain, more fun. Is there special reasons you want to go C/C++/Java?

---

### Post by Tomosaur on 2007-01-03
Please stop with the python evangelism. If he wants to use C/C++/Java, then that's his choice.

---

### Post by moma on 2007-01-03
The Code::Blocks guide is now moved to 
o---> **[http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)**   <---o Go there :-)


---------------- THIS TEXT BELOW IS OBSOLETE AND OLD, NO LONGER IN USE -------------------
---------------- Este texto abaixo não é mais longo no uso ----- (ir) vá a **[http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)**

[COLOR="Silver"]Install necessities
$ sudo apt-get install build-essential subversion

$ sudo apt-get install automake1.9 autoconf libtool

$ sudo apt-get install libxxf86vm-dev libgtk2.0-dev wx-common libwxgtk2.6-0 libwxgtk2.6-dev  wx2.6-examples 

Optionally install wxWidgets version 2.8.  Version 2.8 comes with Ubuntu 7.04.
$ sudo apt-get install libwxbase2.8-dev  libwxgtk2.8-dev  wx2.8-doc   wx2.8-examples   wx2.8-headers  wx2.8-i18n 

$ sudo ldconfig
-------------

Download the latest version of Code::Blocks
$ mkdir $HOME/cb
$ cd $HOME/cb

$ svn checkout [http://svn.berlios.de/svnroot/repos/codeblocks/trunk](http://svn.berlios.de/svnroot/repos/codeblocks/trunk)

Cd into source directory
$ cd trunk

Read instructions
$ cat BUILD

Configure source.
$ ./bootstrap
$ ./configure --enable-contrib

Compile it
$ make

Install it
$ sudo make install
----------------------------------------------

Run & test it 
$ codeblocks 

At first start, select "GNU GCC compiler" from the list.

Where did it put it?  In case you wanna create an icon for C::B?
$ which codeblocks 
----------------------------

**Note 1:**
If you want to develope OpenGL (glut) applications, install FreeGlut first :-)
$ sudo apt-get install freeglut3 freeglut3-dev

In Feisty Fawn (Ubuntu 7.04), get also libxmu-dev and libxxf86vm-dev
$ sudo apt-get install libxmu-dev  libxxf86vm-dev

An important tip: Say: /usr when it asks "Please, Select GLUT's location:" in the Code::Blocks' glut-wizard (project wizard).
Read also the Note 2 below.
------------------------------

**Note 2 !:**
If you want to develope GLFW applications, install GLFW first ( [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) )

And fix a minor bug in Ubuntu 6.06, 6.10 and maybe in 7.04.


EDIT 24.feb.2007:: You can fix the following "Xxf86vm" problem by installing libxxf86vm-dev package.
$ sudo apt-get install libxxf86vm-dev

[[
During compilation of OpenGL , Glut and GLFW apps, the Code::Blocks will complain that it cannot find and link to "Xxf86vm" library.
Ubuntu has Xxf86vm, but it's not sym-linked properly. Does Ubuntu's dev-people know about this "bug" ?
$ locate Xxf86vm
....

This command will fix the error.
$ sudo ln -s /usr/lib/libXxf86vm.so.1  /usr/lib/libXxf86vm.so

You may need to update the cache of dynamic libraries
$ sudo ldconfig 
]]
------------------------------

**Note 3:**
Code::Blocks' source code is updated quite frequently. You can update your version by re-running these commands
$ cd $HOME/cb
$ svn checkout [http://svn.berlios.de/svnroot/repos/codeblocks/trunk](http://svn.berlios.de/svnroot/repos/codeblocks/trunk)
...
...
...
$ sudo make install

Enjoy.
------------------------------

**Note 4 **, c-cpp-reference:
Do not forget to install the "c-cpp-reference" package. Use your Synaptic and get the package. It will put some HTML help files in the  /usr/share/doc/c-cpp-reference/ directory. Start Firefox and open **/usr/share/doc/c-cpp-reference/index.html**

Also these web C/C++ sites are very helpful:
[http://www.cppreference.com/](http://www.cppreference.com/)
+
[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html) 
--------------------------------------------------------------

**Note 5 **, Important GLUT / OpenGL guides: 
[Redbook.html]("http://www.polytech.unice.fr/~buffa/cours/synthese_image/DOCS/trant.sgi.com/opengl/examples/redbook/redbook.html")
([Redbook.html]("http://www.gamedev.net/reference/count.asp?LinkID=993") )
[Bluebook.html ]("http://www.gamedev.net/reference/count.asp?LinkID=611")
[http://www.opengl.org/code/category/C19/]("http://www.opengl.org/code/category/C19/")
[http://nehe.gamedev.net/]("http://nehe.gamedev.net/")
[http://ubuntuforums.org/showthread.php?t=333867#9](http://ubuntuforums.org/showthread.php?t=333867#9)


GLUI = OpenGL based GUI library (buttons, edit boxes, list boxes etc...)
[http://glui.sourceforge.net/]("http://glui.sourceforge.net/")
--------------------------------------------------------------

**Note 6 **, wxWidgets examples: 
WxWidgets examples are installed in  /usr/share/doc/wx2.6-examples/examples/ or  /usr/share/doc/wx2.8-examples/examples/ directories.
Use the "unpack_examples.sh" script (in the same directory) to unpack the samples to your $HOME directory.  For example, run:
$ /usr/share/doc/wx2.8-examples/examples/unpack_examples.sh   $HOME/wxwidgets2.8
--------------------------------------------------------------

**Note 7 **, Other important programming resources: 
[http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)[/COLOR]

---

### Post by suki on 2007-01-03
> **Tomosaur said:**
> Javac is a command line utility, you compile stuff like this:

```

javac myFile.java

```

or ```

javac *.java

```
to compile all .java files in the current directory. It's generally pretty fast unless your processor is slow. There's no graphical popup.

I was aware of the line to compile. The reason I asked about graphical popup is because I developed a small game on Netbeans with Windows and I wanted to see how it ran on Ubuntu. 

Do you happen to know of any java compiler that's useful to see GUI popup?

---

### Post by suki on 2007-01-03
> **pmasiar said:**
> Suki,

Excuse me if I am wrong, but it looks like you are beginnig programmer. We had a [poll ]("http://ubuntuforums.org/showthread.php?t=233405")recently, in opinion of many python is best language for a beginner. Less pain, more fun. Is there special reasons you want to go C/C++/Java?

The reason for such languages is because of courses taken and intend to take put importance on said languages. According to one of my professors "I want you to feel the pain".

---

### Post by suki on 2007-01-03
> **moma said:**
> Start with the Code::Blocks IDE: [http://codeblocks.org/](http://codeblocks.org/)

This is how to tame the Code::Blocks IDE for C/C++ programming in Ubuntu 6.06/6.10.

[COLOR="Magenta"]Install necessities[/COLOR]
$ sudo apt-get install build-essential subversion

$ sudo apt-get install automake1.9 autoconf libtool

$ sudo apt-get install  libgtk2.0-dev wx-common libwxgtk2.6-0 libwxgtk2.6-dev  

$ sudo ldconfig
-------------

[COLOR="Magenta"]Download the latest version of Code::Blocks[/COLOR]
$ mkdir $HOME/cb
$ cd $HOME/cb

$ svn checkout [http://svn.berlios.de/svnroot/repos/codeblocks/trunk](http://svn.berlios.de/svnroot/repos/codeblocks/trunk)

[COLOR="Magenta"]Prepare for it[/COLOR]
$ cd trunk

[COLOR="Magenta"]Read instructions[/COLOR]
$ cat BUILD

[COLOR="Magenta"]Configure source.[/COLOR]
$ ./bootstrap
$ ./configure --enable-contrib

[COLOR="Magenta"]Compile it[/COLOR]
$ make

[COLOR="Magenta"]Install it[/COLOR]
$ sudo make install
----------------------------------------------

[COLOR="Magenta"]Run & test it [/COLOR]
$ codeblocks 

At first start, select [COLOR="SeaGreen"]"GNU GCC compiler[/COLOR]" from the list.

Where did it put it?  In case you wanna create an icon for C::B?
$ which codeblocks 
----------------------------

**Note 1:**
If you want to develope OpenGL (glut) applications, install FreeGlut first :-)
$ sudo apt-get install freeglut3 freeglut3-dev

An important tip: Say: [COLOR="Purple"]/usr[/COLOR] when it asks "Please, Select GLUT's location:" in the Code::Blocks' glut-wizard (project wizard).
Read also Note 2 below.
------------------------------

**Note 2 !:**
If you want to develope GLFW applications, install GLFW first ( [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) )

And fix a minor bug in Ubuntu 6.06 and 6.10.
During compilation of OpenGL , Glut and GLFW apps, the Code::Blocks will complain that it cannot find and link to "Xxf86vm" library.

Ubuntu has Xxf86vm, but it's not sym-linked properly. Does Ubuntu's dev-people have a reason for this bug ?
$ locate Xxf86vm
....

This command will fix the error.
$ sudo ln -s /usr/lib/libXxf86vm.so.1  /usr/lib/libXxf86vm.so

Enjoy.

Very useful, thank you! 
I didn't follow your Note 1 and 2 because I didn't think I would need those two features until much later. But if I do need them, if uses the commands as is would it still be okay even though Code Blocks is already installed?

---

### Post by moma on 2007-01-04
> **suki said:**
> if uses the commands as is would it still be okay even though Code Blocks is already installed?
Yes. 
You can run the commands (in Note 1 and 2) either before or after installation of Code::Blocks.
------

Note:
Code::Blocks' source code is updated quite frequently.  You can update your version by re-running the commands
$ cd $HOME/cb
$ svn checkout [http://svn.berlios.de/svnroot/repos/codeblocks/trunk](http://svn.berlios.de/svnroot/repos/codeblocks/trunk)
...
etc. 
...
$ sudo make install

---

### Post by nsleiman on 2007-01-04
> **suki said:**
> I was aware of the line to compile. The reason I asked about graphical popup is because I developed a small game on Netbeans with Windows and I wanted to see how it ran on Ubuntu. 

Do you happen to know of any java compiler that's useful to see GUI popup?

you can install netbeans5.5 on your ubuntu box and try to compile/launch this prog from it (since it was originally compiled on netbeans/windows). if its a jar try from the console java -jar xxx. 

good luck

---

### Post by Tomosaur on 2007-01-04
I don't understand what you mean by GUI popup. No compiler I've used has done anything except give a text output. Do you mean 'will it compile a GUI program'? The answer is yes. You need to RUN the compiled program, however.

---

### Post by Rui Pais on 2007-01-20
> **moma said:**
> Start with the Code::Blocks IDE: [http://codeblocks.org/](http://codeblocks.org/)

This is how to tame the Code::Blocks IDE for C/C++ programming in Ubuntu 6.06/6.10.

[COLOR="Magenta"]Install necessities[/COLOR]
$ sudo apt-get install build-essential subversion

$ sudo apt-get install automake1.9 autoconf libtool

$ sudo apt-get install  libgtk2.0-dev wx-common libwxgtk2.6-0 libwxgtk2.6-dev  

$ sudo ldconfig
-------------

[COLOR="Magenta"]Download the latest version of Code::Blocks[/COLOR]
$ mkdir $HOME/cb
$ cd $HOME/cb

$ svn checkout [http://svn.berlios.de/svnroot/repos/codeblocks/trunk](http://svn.berlios.de/svnroot/repos/codeblocks/trunk)

[COLOR="Magenta"]Cd into source directory[/COLOR]
$ cd trunk

[COLOR="Magenta"]Read instructions[/COLOR]
$ cat BUILD

[COLOR="Magenta"]Configure source.[/COLOR]
$ ./bootstrap
$ ./configure --enable-contrib

[COLOR="Magenta"]Compile it[/COLOR]
$ make

[COLOR="Magenta"]Install it[/COLOR]
$ sudo make install
          
hi, thanks!!
Many useful. May i suggest an extra option?

Replacing 'sudo make install' with 'sudo checkinstall -D' will create an deb packages 
that make it easier to install and uninstall and/or distribute.
Just need to run and change at the option [2] - name: trunk -> codeblocks
and [3] - Version: '*unacceptable several lines of trunk numbers*' -> something your prefer **on one line**, like -r3511 or 20070120-3511.

And  a nice manageable deb will be produced :)

---

### Post by vlado on 2007-03-02
While trying to compile Code::Blocks from svn, the g++ keeps on finding errors like:
../../../src/include/safedelete.h:18: error: extra ';'
and so on for many other header files...
Is there something wrong with g++ 4.1.2?
Is there some "known" fix for this or just hand fixing all the header files?

thanks

---

