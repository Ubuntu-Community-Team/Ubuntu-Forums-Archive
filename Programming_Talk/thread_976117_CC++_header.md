---
title: "C/C++ header"
date: 2008-11-09
forum: Programming Talk
---

### Post by pavel989 on 2008-11-09
how can i get mouse or keyboard info?

to clear that up; does linux (or ubuntu, to be more in detail) do the windows message thing?

---

### Post by samjh on 2008-11-09
What mouse and keyboard info do you want to get?  The key pressed, mouse button or position, make and model?

What do you mean by windows messaging thing?  You'll find that as Linux doesn't have a universal windowing manager, messages passed to/from windows will depend on the windowing manager used.

---

### Post by pavel989 on 2008-11-09
key pressed, mouse buttons, position. like that, make and model do not matter. and i get that linux has no universal windows manager, but i meant to rather ask, how would an application recieve a message or notification that a button was pressed?

---

### Post by samjh on 2008-11-09
It depends on what interface toolkit is used.

For normal text console programs, you just use your programming language's standard I/O functions.  But if a program involves a GUI (including console GUIs), then it depends on the GUI library used by the program.  Gtk+, Qt, curses, etc., all have their own methods of handling keyboard and mouse inputs.

---

### Post by pavel989 on 2008-11-09
what would u recommend if im working with opengl?

---

### Post by LaRoza on 2008-11-09
> **pavel989 said:**
> what would u recommend if im working with opengl?

Whatever your target audience is using ;)

---

### Post by pavel989 on 2008-11-09
so opengl will work on any toolkit and window manager?

---

### Post by LaRoza on 2008-11-09
> **pavel989 said:**
> so opengl will work on any toolkit and window manager?

I believe you need X for it, but OpenGL will work everywhere it is supported (Linux, Windows, OS X, etc)

---

### Post by gnusci on 2008-11-09
> **pavel989 said:**
> so opengl will work on any toolkit and window manager?

I really recommend you to read a little bit more to make the thinks clear first, I see you are a completely beginner. Here some good links for starting... 

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)
[http://www.visi.com/~grante/Xtut/](http://www.visi.com/~grante/Xtut/)
[http://www.linfo.org/x.html](http://www.linfo.org/x.html)
[http://www.x.org/wiki/](http://www.x.org/wiki/)
[http://xwinman.org/](http://xwinman.org/)

---

### Post by samjh on 2008-11-09
> **pavel989 said:**
> what would u recommend if im working with opengl?

It depends on what you're using for the windowing and user interface portions of your program.  OpenGL is only a graphics library.

For example, you could be using SDL to handle the user display and events.  If so, see the [SDL documentation](http://www.libsdl.org/cgi/docwiki.cgi) on how to handle displays and events.

If you're using OpenGL in conjunction with GTK+, Qt, or whatever else you might be using, you'll need to check documentation for those libraries.

---

