---
title: "Setting up ubuntu for some serious coding"
date: 2007-06-09
forum: Programming Talk
---

### Post by unixguru on 2007-06-09
I will be free with nothing to do for the next 2 months. I want to spend the time and learn some some serous programming. I have my ubuntu machine setup running the command-line version, installed from the alternate cd. For the GUI i am using kde-core. As I have installed only a minimal system, I am surely missing some needed packages like pkg-config . I don't know exactly what packages I am missing so I need you guys to fill me on the packages needed for my purposes. Here are the things I want to do and the pacakges I think I'll need

1. **c/c++ programming**:- I have already installed build-essential package and vim-gtk. I am looking at kdevelop for an ide, though mostly I will be working on the terminal. I need to install some manpages, I am looking at manpages-dev but I heard somewhere that glibc-doc is better than manpages-dev. Can anyone clarify? 
2. **Gtk+ programming in c/c++**:- I think I need dev packages of libgtk and libgtkmm. Any others?
3. **OpenGl and SDL**:- I am confused about opengl. Should libglut3-dev be enough or i need something else. For SDL libsdl-dev should be enough right?
4. **Kde programming**:- kdesdk
5..**Python**:- There are so many packages and I want to know the ones which will be most useful.

---

### Post by leibowitz on 2007-06-09
Please choose one. It's overkill to play with all of that. 

Anyway, AFAIK for development you need:

gcc : C compiler
g++: C++ compiler
python2.x: "python" command line
java jdk: In case you need it, use "javac" for pseudo-compiler, and "java" for the virtual machine.

Then you will need some development libraries like you mentionned.
For GUIs, you will choose one of those I suppose:
- libgtk2.0-dev (Gtk - Gnome)
- libgtkmm-2.x-dev (Gtk C++ bindings)
- libqt4-dev (Qt - KDE)

I think every other required packages will be installed as dependencies of those.

Note: manpages-dev is essential for minimal help about usual functions like strlen() in C, and other things (Bash scripts, etc.) And I don't know about glibc-doc.

But I would say that help/documentation is a necessity if you want to find easily what you are looking for. I have devhelp installed for that purpose, and every documentation package installed is available from that application. I must say the search area is very helpfull.

For SDL you will need: 
- libsdl1.2-dev (base input and audio/video output)
- libsdl-image1.2-dev (if you need to load JPG, Gif, etc.)
- libsdl-mixer1.2-dev (if you need more audio support)
- libsdl-ttf2.0-dev (if you want to use TTF fonts)

SDL doesn't have much documentation package (or I didn't find them) but it's easily accessible from the official website ( [http://www.libsdl.org/docs.php](http://www.libsdl.org/docs.php) )

If you need more: 
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)
[http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)


Have fun coding!

---

### Post by meatpan on 2007-06-09
If you want to learn some linux programming, check out the book, "Beginning Linux Programming" by Stones, Matthew 

The book has quite a few detailed walk through examples and covers major components of linux, including:  graphical/tty programming, filesystems, devices, system-5 interprocess communication facilities, sockets, threading, and kernel modules.

---

### Post by pmasiar on 2007-06-09
> **unixguru said:**
> I will be free with nothing to do for the next 2 months. I want to spend the time and learn some some serous programming. 

You forgot to mention your current skill level in any og mentioned languages, and interests. 

> 5..**Python**:- There are so many packages and I want to know the ones which will be most useful.

Most useful for what? Games? Web-based apps? GUI?

---

