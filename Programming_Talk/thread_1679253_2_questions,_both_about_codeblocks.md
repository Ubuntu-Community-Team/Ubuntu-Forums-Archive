---
title: "2 questions, both about code::blocks"
date: 2011-01-31
forum: Programming Talk
---

### Post by likesoursugar on 2011-01-31
í landi þar sem enginn býr.

---

### Post by Paul820 on 2011-01-31
You can run your program from within codeblocks by clicking the green arrow below the menu bar. Or you can open a terminal and type the full path to the program (or install nautilus-open-terminal). You can also set the file as executable by right-clicking on it select properties->permissions and selecting "Allow executing file as program"

As for the white line, it seems you are using a black theme so you will have to got to (in codeblocks) settings->editor on the left click syntax highlighting and mess with the colours on there.

---

### Post by Tony Flury on 2011-02-01
> **likesoursugar said:**
> Hi. I'm a new linux user, been using windows for years but now it's time to go over to linux. I'm a c++ programmer and want some kind of IDE, code::blocks. But I have 2 questions.

1. I said I was a new linux user so I don't know exactly how the executable files work but shouldn't a console pop up when I double click my program I compiled? I mean in the Home dir where I have the project.


Unlike DOS/windows, under linux an executable program wont automatically open a terminal window. If your progame generates terminal output that you want to see, then you need to run it in a terminal, set its launcher to open a terminal (and make sure your program keeps the terminal open when it has finished so you can read the output), or write your program so that is specifically opens a terminal and writes to it.

---

### Post by likesoursugar on 2011-02-01
í landi þar sem enginn býr.

---

### Post by fct on 2011-02-01
If you want to do graphics programming a la directdraw/direct3d, then libsdl ( [http://www.libsdl.org](http://www.libsdl.org) ) plus opengl calls is what you'll most probably prefer.

When it comes to UI programming with buttons and such, you should go for a multi-platform toolkit. The best ones for C++ are Qt and wxwidgets. GTKmm too.

Edit: as far as I remember, Code:blocks has wizards for both Qt and SDL projects.

---

### Post by likesoursugar on 2011-02-01
í landi þar sem enginn býr.

---

### Post by SledgeHammer_999 on 2011-02-01
> **likesoursugar said:**
> Ok thanks, Yes i've been using SDL for my windows apps too, to create windows. But I don't like that. I want full controll like when you're using the win32 api. There isn't any linux api?

You're looking for GUI toolkits. There isn't a standard linux toolkit for that. The 2 most popular are [Gtk+](http://www.gtk.org/) and [Qt](http://qt.nokia.com/products/). Gtk+ is written in C but has bindings for lots of other languages. eg the C++ bindings are called [Gtkmm](www.gtkmm.org). Qt is written in C++ and it also has bindings for other languages.

Gnome, Xfce and Lxde use Gtk+ and KDE uses Qt. BUT you can use Qt apps in Gnome/Xfce/Lxde without problem and the same goes for gtk apps and KDE.

If you're looking to crossplatform stuff, then both Gtk+ and Qt can be used on windows too. The general consencus is that it is far easier to build Qt for windows than Gtk for windows.(both offer prebuild packages for windows). But the biggest contender(by popularity) for crossplatform GUIs is [WxWidgets](www.wxwidgets.org).

So a GENERAL rule of thumb is, if you use a certain DE then code in it's **preferred** toolkit. Eg Gtk/gtkmm for Gnome,Xfce,Lxde and Qt for KDE. HOWEVER if you want your app to be used by people using other DEs then don't use DE-specific api(like gconf apis for GNOME). In this case your application will still work on other DEs but it will require additional libraries to be installed(the DE-specific ones) which generally can be characterised as uneccessary bloat.

---

