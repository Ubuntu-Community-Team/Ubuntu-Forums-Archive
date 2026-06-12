---
title: "Help out the Ubuntu Documentation Team"
date: 2006-02-04
forum: Programming Talk
---

### Post by Luffield on 2006-02-04
The Ubuntu Documentation Team seems to need some help with the Programming part of the Desktop Guide for the next version of Ubuntu, 6.04. The original call for help can be found [here]("http://www.ubuntuforums.org/showthread.php?t=123836"). I noticed that the [Programming]("http://doc.ubuntu.com/ubuntu/desktopguide/C/ch03s05.html") part of the guide is far from being complete and after I commented about it I was asked to help out. Since I'm not a programmer (I learned programming and wrote MATLAB scripts when I did my M.Sc., but never really did it for a living) and I'm not femilar with the IDEs avialble for Ubuntu, I thought I'd ask for your help here.

I took a look at the thread called "What's your favorite IDE" and found a few names that showed up a lot. So here's my first draft, I gotta leave home in a few minutes so it's kinda lame, but I wanted to get it (half :)) done before I leave.

Any comments, corrections and suggestions will be appreciated.


----------------------------------------------
Anjuta is a versatile Integrated Development Environment (IDE) for C and C++ on GNU/Linux.
[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)


Eclipse is an open source community whose projects are focused on providing a vendor-neutral open development platform and application frameworks for building software.
[http://www.eclipse.org/](http://www.eclipse.org/)


The KDevelop-Project aims to build up an easy to use IDE for KDE. KDevelop supports many programming languages.
[http://www.kdevelop.org/](http://www.kdevelop.org/)


MonoDevelop is a free GNOME IDE primarily designed for C# and other .NET languages.
[http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)


NetBeans is an open-source project dedicated to providing rock solid software development products.
[http://www.netbeans.org/index.html](http://www.netbeans.org/index.html)

---

### Post by ow50 on 2006-02-04
Here's a list of useful applications for those of use who hate IDEs. One application per task. Something you might or might not want to mention. The descriptions below are written by me. See the links for the official word.

I assume the desktop guide covers mostly Ubuntu (the GNOME version). These are all GTK apps (except stable versions of emacs) and fit well in GNOME.

**Emacs, Vim**
[http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/)
[http://www.vim.org/](http://www.vim.org/)
Well known and popular multi-purpose programming editors. Steep learning curve.

**Glade**
[http://glade.gnome.org/](http://glade.gnome.org/)
GUI designer to create GTK user interfaces. Generates a .glade XML file that contains all the widgets and their properties. The Glade file can then be imported in any popular (one that has GTK bindings) programming language code. You could mention wx and Qt designers as well, if they are usable.

**Devhelp**
[http://developer.imendio.com/wiki/Devhelp](http://developer.imendio.com/wiki/Devhelp)
View any documentation installed on your hard drive. For example, after installing package "python-doc" you can view the official Python documentation with Devhelp.

**Gnome Terminal**
Use this to compile and run your code.

**Regexxer**
[http://regexxer.sourceforge.net/](http://regexxer.sourceforge.net/)
Powerful search and replace tool for multiple files using regular expressions. Makes it easy to rename some variable in all files.

**Meld**
[http://meld.sourceforge.net/](http://meld.sourceforge.net/)
Graphic diff and merge tool. Useful to compare files. Works at least with CVS and SVN.

---

### Post by Luffield on 2006-02-05
Cool, thanks ow50.
More input, especially about IDEs, would be most welcome. Didn't I miss any major IDE?

---

### Post by majikstreet on 2006-02-05
**Eric3 Python IDE**
"eric3 is a full featured Python (and Ruby) IDE that is written in PyQt using the QScintilla editor widget."

**IDLE**
"IDLE is the Python IDE built with the Tkinter GUI toolkit."

---

### Post by ow50 on 2006-02-05
What comes to IDEs, I think the main emphasis should be on Anjuta, Eclipse and KDevelop (if the guide covers Kubuntu). Maybe a couple Python- and Java-specific ones might be worth a mention (I wouldn't know which ones).

Also HTML editors/IDEs could be mentioned. Nvu, Bluefish, Screem and Quanta Plus come to mind.
[http://www.nvu.com/](http://www.nvu.com/)
[http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)
[http://www.screem.org/](http://www.screem.org/)
[http://quanta.kdewebdev.org/](http://quanta.kdewebdev.org/)

---

### Post by majikstreet on 2006-02-05
**Bluefish**
Cool IDE that's not just for HTML! Many other languages are supported.

---

### Post by macewan on 2006-02-06
Stetic, which will hopefully be part of Monodevelop, looks promising:
[INDENT]You can use Glade along with the Glade# bindings to easily design GUI applications. A new GUI designer called [SIZE=3]_**Stetic**_[/SIZE] is being built which will be integrated with the MonoDevelop IDE.
via: [Mono-project]("http://www.mono-project.com/Mono,_a_technical_whitepaper")
[/INDENT] ----------------------------------------------
[Eclipse]("http://www.eclipse.org/") is another.

---

### Post by Luffield on 2006-02-07
&#8206;thanks guys.

---

### Post by mattheweast on 2006-02-08
Ok, I have inserted a list of stuff into the guide: please let me know any feedback or comments on how to improve that section!

[http://doc.ubuntu.com/ubuntu/desktopguide/C/ch03s05.html](http://doc.ubuntu.com/ubuntu/desktopguide/C/ch03s05.html)

Thanks, Matt

---

### Post by rich on 2006-02-09
Good stuff. 

One omission might be stani's python editor.
[http://stani.be/python/spe/blog/](http://stani.be/python/spe/blog/)

"Spe is a free python IDE with auto indentation & completion, call tips, syntax coloring & highlighting, UML diagrams, class explorer, source index, auto todo list, sticky notes, pycrust shell, file browsers, drag&drop, context help, Blender support, ... Spe ships with Python debugger (remote & encrypted), wxGlade (gui designer), PyChecker (source code doctor) and Kiki (regex console)."

I've just started playing with it and I'm having the love. I'm trying not to be impressed by how pretty it is (but it is).

Also worth a mention as Stani is an ubuntu member and is talking about making ubuntu-tailored versions. 

I'm not sure from reading your list whether it's restricted to "communities"...

cheers,
Rich

---

### Post by thumper on 2006-02-09
I second SPE :)

---

### Post by stani on 2006-02-11
As I start using Ubuntu (xubuntu) myself, of course I support any iniative which brings SPE closer to Ubuntu.

Stani
---
SPE lead developper 
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by sas on 2006-02-13
Thanks for all the IDEs mentioned.

Are there any programming tutorials/references that stand out as having been useful to you that are suitable to be linked from the programming section? 

I'm thinking along the lines of "How to develop a Gnome application using Glade" or "How to develop a KDE Application in C++"  for example.

Articles regarding Python may perhaps be the most suitable, however I'm keen to hear about other languages too.

---

### Post by stani on 2006-02-14
Good Python tutorials, you can find on [http://www.serpia.org](http://www.serpia.org)

There is also a tutorial about SPE (Python IDE): [http://www.serpia.org/spe](http://www.serpia.org/spe)

Good Python videos are available at [http://www.showmedo.com](http://www.showmedo.com)

with two SPE videos: [http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE](http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE)

Stani
--
SPE [http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by Malakim on 2006-02-20
There are a few KDE / KDevelop tutorials available at [the KDevelop site]("http://www.kdevelop.org/index.html?filename=3.3/tutorials.html"), which might be usefull. The most usefull to a KDE / KDevelop beginner (with some C++ knowledge) would probably be this one: [The KDevelop Programming Handbook]("http://docs.kde.org/development/en/kdevelop/kde_app_devel/")

Regards,
Markus Svensson

---

