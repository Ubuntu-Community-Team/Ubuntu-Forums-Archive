---
title: "FAQ: GUI Toolkits for Linux"
date: 2008-04-28
forum: Programming Talk
---

### Post by LaRoza on 2008-04-28
There are many GUI toolkits available for many languages. Many of them work cross platform and with many languages.

My wiki has a section for each GUI toolkit for each language in the [Programming Library](http://laroza77.wikidot.com/librarylibrary#toc4)

Common toolkits:

[list]
[*] [GTK+]("http://en.wikipedia.org/wiki/GTK") - It is in C and has been ported to many languages. GNOME and Xfce use GTK. [Glade]("http://glade.gnome.org/") can be used to design GUI's in GTK.
[*] [QT]("http://en.wikipedia.org/wiki/Qt_(toolkit)") - It is in C++, and has been ported to many languages. KDE uses QT. [QT Designer]("http://trolltech.com/products/qt/features/designer") can be used to design GUI's in QT.
[*] [wxWidgets]("http://en.wikipedia.org/wiki/WxWidgets") - It is meant to look native cross platform. It is in C++, but also has been ported. [wxGlade]("http://wxglade.sourceforge.net/") can be used to design GUI's.
[*] [Tk]("http://en.wikipedia.org/wiki/Tk_(framework)") - This is (as far as I know, please correct if I am wrong) a toolkit used by scripting languages mostly. Tcl and Tk are easily used with each other. Python, Perl, PHP, and Ruby can use Tk also. It is the default Python GUI toolkit as well (as Tkinter). It is cross platform, but it is not the best looking toolkit. 
[/list]

[list]
[*] **Python**, [EasyGUI]("http://www.ferg.org/easygui/") provides the simplest GUI solution. (It uses Tkinter)
[*] **Shell** scripts, [Zenity]("http://www.linuxmanpages.com/man1/zenity.1.php") provides useful widgets. 
[*] **Java** can use other toolkits, but [Swing]("http://en.wikipedia.org/wiki/Swing_(Java)") is part of Sun Microsystems' Java Foundation Classes.
[/list]

---

### Post by stevescripts on 2008-04-28
Just a little FYI re Tk.

Easily embedded in C/C++ programs to provide the GUI. (this also allows a scripting
interface to your C/C++ programs via tcl, which I find quite useful)

I will hack out a clean little example and post it somewhere soon.

Using Tk with Java requires jacl or tclblend.  (Plenty of folks do this, but
I find it a real PITA)

Steve

---

### Post by LaRoza on 2008-04-28
> **stevescripts said:**
> Just a little FYI re Tk.

Easily embedded in C/C++ programs to provide the GUI. (this also allows a scripting
interface to your C/C++ programs via tcl, which I find quite useful)

I will hack out a clean little example and post it somewhere soon.

Using Tk with Java requires jacl or tclblend.  (Plenty of folks do this, but
I find it a real PITA)

Steve
I knew you'd know. Is using Tk like that common?

Could you post a few links to tutorials or references? (My wiki is bare on that part)

---

### Post by WW on 2008-04-28
[FLTK](http://www.fltk.org/) is also an option.

---

### Post by stevescripts on 2008-04-28
> **LaRoza said:**
> I knew you'd know. Is using Tk like that common?

Could you post a few links to tutorials or references? (My wiki is bare on that part)

Yes, that is a common use for Tk. I know many folks, whose primary use of tcl/tk is embedded in C/C++ programs.

I apologize for not finding time to update your wiki.  Have been extremely
busy with paywork.

Rather than some existing links, thought I would hack out something clean...

Steve

---

### Post by mssever on 2008-04-28
You should add to your notes about Tk that it's ugly and has usability issues.


[LIST=1]
[*]Aesthetics: The look of the Tk version that ships with Python is a throwback to the bad old days of Motif where it's no wonder that many UNIX users didn't use X. Absolutely hideous. I've been to the Tk website and seen screenshots of the current themes. The look for Windows XP is reasonable, but otherwise, it's no better. The  *nix choice is between a GTK1-like theme and a few outdated-KDE-like themes. Nothing current, and nothing that follows the actual theme in use.
[*]Usability: Tk is also seriously broken when it comes to usability. For example, when you open a menu, then move your mouse to a submenu or another regular menu, that menu doesn't open until you click on it. Clearly, this is broken. Every other toolkit on every OS I've used behaves sensibly, with the menu following the mouse.
[/LIST]
This is why I question whether Tk is the best solution to any problem. It's just too broken to be useful.

---

### Post by stevescripts on 2008-04-28
The community is aware of the issues that a lot of folks have with the appearance of
Tk, and is actively working on it.

As mssever notes, it does currently look better on XP than Linux (since the advent of
8.5.x and the inclusion of the tile widgets.) Nearly all of my programming paywork is for windows, FWIW ...

Tkinter is doable with 8.5 - I will have to find the link again ...

My personal preference for Tk, well - I am old, and not much into eye candy 
(everything looks better than computer output on green/white bar paper... ;) )
and the BSD license.

Steve
@mssever  - just thought I would let you know, that I really appreciate your
input on this forum ... of course this goes for a lot of the other regulars here as well
also (an afterthought..) feel free to contact me concerning the usability issues you have with Tk - although I don't hack the core, I am in daily contact with the folks who do

---

### Post by mssever on 2008-04-28
> **stevescripts said:**
> also (an afterthought..) feel free to contact me concerning the usability issues you have with Tk - although I don't hack the core, I am in daily contact with the folks who do
What I don't know is if those issues have been solved in recent Tk releases. My only experience with Tk is running Python programs that use Tkinter. I understand that Python doesn't use the latest version of Tk. Also, I've never actually written Tk code. Tk's look has caused me to not even consider it. So I don't know if there are workarounds or even if the code was badly-written.

If they've been solved, great. If not, my comments stand. If there's anything helpful I can do, let me know. PySol is the only Python/Tk program that I've used recently.

Note also that I don't know Tcl.

---

### Post by LaRoza on 2008-04-28
> **mssever said:**
> 
Note also that I don't know Tcl.

Tcl is a neat little language.

---

### Post by mssever on 2008-04-28
> **LaRoza said:**
> Tcl is a neat little language.
I don't know much about it, although it seems to be a bit more string-focused than I'd prefer (maybe that's just my experience with Bash coming back to haunt me). It does appear, though, that it could be easily used in a functional style. Is that correct?

---

### Post by stevescripts on 2008-04-29
> **mssever said:**
> I don't know much about it, although it seems to be a bit more string-focused than I'd prefer (maybe that's just my experience with Bash coming back to haunt me). It does appear, though, that it could be easily used in a functional style. Is that correct?

Yes. Most of my work uses a functional style, and is event-driven.

Also, the Tcl community is putting OO in the core soon, to try
to mitigate the criticism of a lack of OO in Tcl.  There do exist,
however, several high quality OO systems for tcl/tk.  

Personally, when I need OO, I do it in C++, and embed tcl as a scripting language for the app, an Tk for the GUI.

I find using Tkinter somewhat of a PITA (still trying to get
a bit comfy with Python, mostly driven by its high usage here).
Also, I find using PerlTk even ... more difficult (for me, that is)

I will dig out the link for using 8.5 with Tkinter - just busy here.
     TileWrapper - [http://tkinter.unpy.net/wiki/TileWrapper](http://tkinter.unpy.net/wiki/TileWrapper)

TY for the offer to help, in general, the most helpful thing that folks could do that are not familiar with tcl and tk, is to occasionally d/load the release candidates, run the tests, and
report failures.

One criticism of tcl/tk that I definitely agree with, is the lack of a consolidated repository (ala CPAN).  Useful extensions, OO systems and other things, are scattered wildy about the web...

Steve

---

### Post by pmasiar on 2008-04-30
"There are two types of integrated development environments (IDE) in the world. That is convenient, because there are two types of developer in the world."

[Sean McGrath, W3C's Expert](http://www.itworld.com/AppDev/software-development-ide-nlstipsm-080429/index.html)

I too prefer the "lumberjack" solution :-)

---

### Post by Ned_in_Vancouver on 2008-05-21
I've written a C program that runs on a small WinXP HPCC.

We're looking at converting our development work to Linux. I've installed Ubuntu 8.04 on a 32bit Intel test platform and have ported several parts of our ap to Eclipse. Preliminary tests show a 30% speed improvement. Excellent.

We need to upgrade one part of our ap to GUI, the front-end. I'd like to find a GUI app that works with C, ideally both in a Visual Studio (WinXP) and Eclipse/Ubuntu platforms. If I have to use C++ for the front end that's OK. Our goal is speed of execution and (temporarily) cross platform deployment.

Any ideas?

Many thanks. I'm a Linux newbie, but liking it a lot.

---

### Post by LaRoza on 2008-05-21
> **Ned_in_Vancouver said:**
> I've written a C program that runs on a small WinXP HPCC.

We're looking at converting our development work to Linux. I've installed Ubuntu 8.04 on a 32bit Intel test platform and have ported several parts of our ap to Eclipse. Preliminary tests show a 30% speed improvement. Excellent.

We need to upgrade one part of our ap to GUI, the front-end. I'd like to find a GUI app that works with C, ideally both in a Visual Studio (WinXP) and Eclipse/Ubuntu platforms. If I have to use C++ for the front end that's OK. Our goal is speed of execution and (temporarily) cross platform deployment.

Any ideas?

Many thanks. I'm a Linux newbie, but liking it a lot.

Try using GTK?

---

### Post by jespdj on 2008-05-21
> **LaRoza said:**
> [list]
[*] **Java** can use other toolkits, but [Swing]("http://en.wikipedia.org/wiki/Swing_(Java)") is part of Sun Microsystems' Java Foundation Classes.
[/list]
Swing *is* the Java Foundation Classes. The name "Swing" was an internal code name at Sun when they were developing it (10 years ago or so) - the name "Java Foundation Classes" was meant as the official name, but in reality everybody calls it Swing instead of JFC.

Swing was added to Java in version 1.2. Before Swing, there was AWT (Abstract Windowing Toolkit), and Swing is built on top of AWT. Swing has pluggable look-and-feels: the default Swing look-and-feel doesn't look like the native look-and-feel of your OS, but for each of the major platforms (Windows, OS X, GNOME, others) there are native look-and-feels included with Swing.

Another GUI toolkit for Java is SWT ([Standard Widget Toolkit]("http://www.eclipse.org/swt/")), which was originally developed for Eclipse, but which you can also use in your own programs. SWT is a thin wrapper around the OS-native GUI so it performs well and looks native.

There is also a GTK+ binding for Java: [java-gnome](http://java-gnome.sourceforge.net/).

I recently read a book about [FXRuby]("http://www.fxruby.org/"), a GUI toolkit for Ruby, which is based on the [FOX Toolkit]("http://www.fox-toolkit.org/"), a portable C++ GUI toolkit.

---

### Post by dhimes on 2008-07-08
Why does my java desktop app gui look so crappy in Linux?  Both Ubuntu and Fedora don't render the swing widgets well.  I'm pretty new to Linux, and hacked the java on Win XP (so I may have tunnel vision).  Any thoughts are appreciated!

---

### Post by LaRoza on 2008-07-08
> **dhimes said:**
> Why does my java desktop app gui look so crappy in Linux?  Both Ubuntu and Fedora don't render the swing widgets well.  I'm pretty new to Linux, and hacked the java on Win XP (so I may have tunnel vision).  Any thoughts are appreciated!

You'll have to give more information. What toolkit? Version? What is the code for the GUI?

You might want to start your own thread about styling Java apps.

---

### Post by tinny on 2008-07-08
> **dhimes said:**
> Why does my java desktop app gui look so crappy in Linux?  Both Ubuntu and Fedora don't render the swing widgets well.  I'm pretty new to Linux, and hacked the java on Win XP (so I may have tunnel vision).  Any thoughts are appreciated!

That's because you need to manually set a Swing application to use the native look and feel of the OS its running on (By default Swing applications use the Metal look and feel). FYI [http://www.osnews.com/story/10633]("http://www.osnews.com/story/10633") (I dont agree with everything this article says)

You also need to manually turn on things like anti aliasing.

Swing is just fine for developing GUI if you know how to use it. In fact you can easily develop GUI so good that the user would never know that it is not a "native" application.

---

### Post by tinny on 2008-07-08
In terms of Java GUI development I think it is also worth mentioning the [Substance]("https://substance.dev.java.net/see.html") look and feel library. I have used this  library in the past with great success. It gives you very fine grained control of how your swing applications can be themed. These themes (look and feels) are platform independent so you can make your application look the same regardless of the OS they are running on.

---

### Post by dhimes on 2008-07-08
Thanks for the link!

> **tinny said:**
> That's because you need to manually set a Swing application to use the native look and feel of the OS its running on 

I do!  

> **tinny said:**
> 
You also need to manually turn on things like anti aliasing.

I do that too!


> **tinny said:**
> In fact you can easily develop GUI so good that the user would never know that it is not a "native" application.

That's what I'm getting at (works fine on Windows XP & Vista).  I'll read your link.  Thanks again.

---

### Post by tinny on 2008-07-08
> **dhimes said:**
> Thanks for the link!



I do!  


I do that too!




That's what I'm getting at (works fine on Windows XP & Vista).  I'll read your link.  Thanks again.

Can you start another thread ("Making Java GUI's look good") so that we don't hijack this one.

---

### Post by Kadrus on 2008-07-20
**Common Lisp Graphics Toolkit**
**_SLIK_**:The Simple Lisp interface Kit([Radonc.washington.edu]("http://www.radonc.washington.edu/medinfo/prism/"))
**_Garnet_**:Garnet is user interface development environement and Graphic Toolkit for Common Lisp([Garnet Home Page)]("http://www.cs.cmu.edu/afs/cs.cmu.edu/project/garnet/www/garnet-home.html")
**_Ltk_**:LTK is a Common Lisp binding for the Tk graphics toolkit([Ltk Home Page]("http://www.peter-herth.de/ltk/"))
**_CLUE_**:The Common Lisp User Interface Environment([CLUE Download]("http://www-cgi.cs.cmu.edu/afs/cs/project/ai-repository/ai/lang/lisp/gui/clue/")
--
And for more resources on Common Lisp go to:[**Cliki**]("http://www.cliki.net/index")

---

### Post by bruce89 on 2008-07-20
GTK+ has a '+' on the end. Also, Glade is depreciated in favour of GtkBuilder (or ought to be).

---

### Post by mssever on 2008-07-20
> **bruce89 said:**
> GTK+ has a '+' on the end. Also, Glade is depreciated in favour of GtkBuilder (or ought to be).
I think you mean libglade is on the way out. Glade will eventually output GtkBuilder XML files directly. Until then, it's trivial to convert Glade files to GtkBuilder files.

---

### Post by Uchiha_madara on 2008-09-10
thank you a lot

---

### Post by rich1939 on 2008-12-01
I guess I'm really too much of an old-timer...but is there support in Ubuntu for curses? I'm new to Linux, but have used the curses libs in Unix many moons ago and am just now starting to get up to speed with Intrepid.

I see that there is a /lib/libncurses.so.5.6 ...but I can't find curses.h or don't really know what the ".so" refers to. Is this a package that I need to unpack somehow? Or, what do I need to do to use curses or ncurses?

I **do** plan to get up to speed with GTK+...but I was planning on starting with curses and then move up from there.

Sorry to bring down the level of the thread with this **very old** topic.

---

### Post by nvteighen on 2008-12-01
> **rich1939 said:**
> I guess I'm really too much of an old-timer...but is there support in Ubuntu for curses? I'm new to Linux, but have used the curses libs in Unix many moons ago and am just now starting to get up to speed with Intrepid.

I see that there is a /lib/libncurses.so.5.6 ...but I can't find curses.h or don't really know what the ".so" refers to. Is this a package that I need to unpack somehow? Or, what do I need to do to use curses or ncurses?

I **do** plan to get up to speed with GTK+...but I was planning on starting with curses and then move up from there.

Sorry to bring down the level of the thread with this **very old** topic.
libncurses.so **is** the New Curses (ncurses) library. To install the header file, do:
```

sudo apt-get install libncurses5-dev

```

Debian and Debian-based distros separate development files (headers and static libraries) from the main package and usually are found by appending '-dev' to the original package.

---

### Post by mmix on 2008-12-01
[http://www.directfb.org/](http://www.directfb.org/) : Framebuffer GUI SDK

[http://www.diskohq.org/](http://www.diskohq.org/) : directfb based framework

---

### Post by samjh on 2008-12-01
Don't forget [SWT](http://www.eclipse.org/swt/) for Java.

---

### Post by rich1939 on 2008-12-01
> sudo apt-get install libncurses5-dev

Thanks very much. Looks like it installed.

---

### Post by rich1939 on 2008-12-02
Okay...I finally bit the bullet and bought the "Foundations of GTK+ Development" book and am looking forward to programming in C/GTK+.

My initial problem is: how do I install GTK+ and all of the necessary dependent modules, including Glade?

I looked in the Ubuntu Intrepid Package Manager and saw a lot of entries for GTK, but don't know which to choose. Is there a better way to get what I need (e.g., sudo apt-get install gtk+...or something like that)?

---

### Post by bruce89 on 2008-12-02
> **rich1939 said:**
> Okay...I finally bit the bullet and bought the "Foundations of GTK+ Development" book and am looking forward to programming in C/GTK+.

My initial problem is: how do I install GTK+ and all of the necessary dependent modules, including Glade?


Glade is not a dependency of GTK+. In fact, it's depreciated now in favour of GTK+'s GtkBuilder.

Anyway, you need *libgtk2.0-dev* and if you really want to use something that is depreciated, *libglade2.0-dev*. To view the documentation, install *devhelp* and at least *libgtk2.0-doc*.

---

### Post by mssever on 2008-12-02
> **bruce89 said:**
> Glade is not a dependency of GTK+. In fact, it's depreciated now in favour of GTK+'s GtkBuilder.

Anyway, you need *libgtk2.0-dev* and if you really want to use something that is depreciated, *libglade2.0-dev*. To view the documentation, install *devhelp* and at least *libgtk2.0-doc*.
Is Glade really deprecated? My understanding is that libglade is deprecated, not Glade itself, and that Glade will be modified to output GtkBuilder files. In the interim, there's a program to convert libglade XML files to GtkBuilder XML files.

---

### Post by slavik on 2008-12-02
> **mssever said:**
> Is Glade really deprecated? My understanding is that libglade is deprecated, not Glade itself, and that Glade will be modified to output GtkBuilder files. In the interim, there's a program to convert libglade XML files to GtkBuilder XML files.
you are correct.

---

### Post by rich1939 on 2008-12-03
> I too prefer the "lumberjack" solution 

I recently installed the Anjuta IDE and tried creating a project for a "Hello World" application using it. I was **appalled** by the number of cryptic files that it generated. I enjoy using an IDE for program development, but Anjuta goes much too far in the number of files and file-types that it generates.

I'm looking for an IDE that's more like (if you'll pardon the expression) Visual C++ or Delphi for Windows. Does such an IDE exist (for C or C++ development) with Ubuntu, using GTK+?

---

### Post by slavik on 2008-12-03
Anjuta uses GNU make tools for it's projects. What cryptic files are you referring to?

---

### Post by mssever on 2008-12-03
> **rich1939 said:**
> I recently installed the Anjuta IDE and tried creating a project for a "Hello World" application using it. I was **appalled** by the number of cryptic files that it generated. I enjoy using an IDE for program development, but Anjuta goes much too far in the number of files and file-types that it generates.

I'm looking for an IDE that's more like (if you'll pardon the expression) Visual C++ or Delphi for Windows. Does such an IDE exist (for C or C++ development) with Ubuntu, using GTK+?
This thread is about GUI toolkits, not IDEs (as the thread title indicates). If you look through the stickies, you'll find at least one thread on IDEs. A search will turn up many such threads.

---

### Post by bruce89 on 2008-12-03
> **mssever said:**
> Is Glade really deprecated? My understanding is that libglade is deprecated, not Glade itself, and that Glade will be modified to output GtkBuilder files. In the interim, there's a program to convert libglade XML files to GtkBuilder XML files.

Yes, my mistake.

> **slavik said:**
> Anjuta uses GNU make tools for it's projects. What cryptic files are you referring to?

The GNU autotools make/use some very scary looking files.

---

### Post by Namtabmai on 2008-12-03
> **LaRoza said:**
> 
[*] [wxWidgets]("http://en.wikipedia.org/wiki/WxWidgets") - It is meant to look native cross platform. It is in C++, but also has been ported. [wxGlade]("http://wxglade.sourceforge.net/") can be used to design GUI's.
[/list]


This should really be expanded on, "meant to look native" is a little misleading, but also sort of true.
wxWidgets does use the native widget toolkit on each platform. So on Linux is uses GTK, Windows the Win32 widgets and carbon on OS X. So in this respect wxWidgets is a native GUI. Unfortunately it's hard, almost impossible, to get the widgets laid out so that it looks native on each platform.
So because of this layout problem, while the widgets look correct. the whole application and the placement of widgets never feels quite right.


The real question you should ask yourself when developing a cross platform application is what your main priority is in this area.

Cheap development (both in terms on money and time)
or
Applications that feel right on each platform.

Unfortunately even with the best of GUI toolkits these two will always be mutual exclusive. It's not just are you using a native widget toolkit or not, but because of issues like platform HDI guidelines. These aren't the same on every platform (obviously) and no GUI toolkit will every be able to cope with generating interfaces that match these on each platform using a single set of code (at least a single set of manageable code ;) )

---

### Post by rich1939 on 2008-12-03
> **slavik said:**
> Anjuta uses GNU make tools for it's projects. What cryptic files are you referring to?
I was so appalled that I put the entire directory structure in the trash. In retrospect, the primary directory had at least 20-30 files of various types. There was also a ./src directory that had only the Glade source file, the .c file, and probably a couple of header files. I was so distressed by the number of project-related files that I didn't look very carefully at any of them...and the project didn't compile.

I'm sure that the compile errors had something to do with my lack of understanding of Ajunta.

Also, after I exited from the Ajunta program, each time I tried to re-invoke it, it never again brought up the main windows, and, instead, it put up a dialog asking me to choose a program to handle the Glade file (I think). In any case, I had to reboot before I could re-invoke the Ajunta program, and for it to display its main window and menus.

I'm somewhat less that thrilled with using this tool...but am open-minded enough to give it another try if there is a tutorial somewhere that shows, step-by-step how to create a new project and its files for C/GTK+.

---

### Post by bruce89 on 2008-12-03
To be honest, for simple projects, a good old Makefile like this is good enough:

```

CC = gcc
CFLAGS = -g -Wall `pkg-config --cflags --libs gtk+-2.0`

all: program

program: program.c
	$(CC) $(CFLAGS) -o program program.c

clean:
	$(RM) program

```

---

### Post by jmehdi on 2009-06-01
I'm looking for a grid UI component with grouping/filtering/child tables features (like this [.NET component]("http://www.telerik.com/products/winforms/gridview.aspx")); does it exist in the linux world? 

And are there commercial UI toolkits for Linux?

---

### Post by sephirot_5 on 2009-12-21
> **jmehdi said:**
> I'm looking for a grid UI component with grouping/filtering/child tables features (like this [.NET component]("http://www.telerik.com/products/winforms/gridview.aspx")); does it exist in the linux world? 

And are there commercial UI toolkits for Linux?

Qt is a really very nice Toolkit, it comes as lgpl or commercial. It does have grid widgets and a nice RAD like IDE: [qtcreator]("http://qt.nokia.com/products/developer-tools").

---

### Post by d3v1150m471c on 2010-10-23
you can also use bash commands in the glade interface designer although it limits your options. gtkdialog is also an excellent tool for widgets and you can contain the xml file in a bash variable and pipe it into gtkdialog all in one script.

---

