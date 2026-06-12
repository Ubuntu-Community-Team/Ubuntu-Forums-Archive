---
title: "Windows to Ubuntu programmer"
date: 2012-05-24
forum: Programming Talk
---

### Post by thedardanius on 2012-05-24
hi,

I'm new to programming on ubuntu. I have experience on windows ( a lot, with C/C++) but now I face some serious problems with my game engine ( IM trying to convert it into a linux version)

I use glX to display the window. But some questions:
Is there a decent tutorial on how to code on ubuntu using the gcc compiler on code::blocks, from the start to the beginning on how to create a linux window with opengl support?
Also, is there a standard API (like on windows) which can be used to retrieve the widht and height of the screen, and to create a messagebox like on windows (MessageBox(int etc.) functions maybe?).
Also, dont you need ot link to a static library when using opengl?? and for using glut, do you need a dll???so a .so???
please guys, i need to knwo this all!!!

---

### Post by thedardanius on 2012-05-24
also, additionally, how do I maximize and minize a linux window?

---

### Post by roelforg on 2012-05-24
> **thedardanius said:**
> also, additionally, how do I maximize and minize a linux window?

Depends on the de.
In gnome (the default ubuntu de), there are buttons on the left top (instead of right, where windows has them).
If it's maximized, you hover your mouse in the top left screen corner for the buttons to become visible again.

---

### Post by pbrane on 2012-05-24
You are porting a game engine? What is the Windows version using to display graphics? DirectX, OpenGL? If you used OpenGL you shouldn't have a lot to do.

As far as a GUI toolkit there are several. Gtk (Gtkmm for C++) on gnome, Qt on KDE, etc.

There are many tutorials on opengl and glut, google is your friend. Also have a look at [SDL]("http://www.libsdl.org"). SDL is a good toolkit for creating windowed/fullscreen games using opengl.

You don't need to statically link to opengl or glut.

---

### Post by thedardanius on 2012-05-25
guys,
 
I want to use glx ofr window managed, and how do I maximize and minimize a windows programmically (so by useing an API or sth?)
please help me:
I'm using C++ and openGL, glx for window, I need to find an API to maximize and minimize a window and how to retrieve the real widht of the screen + the height, also, BSD socket etc. and a tutorial on how ubuntu basiacally works and how to program on it.

---

### Post by xytron on 2012-05-25
GLX is the interface for connecting OpenGL to the X Window System, that is basically all it does. 

If you only wish to use GLX then to create and manage the GLX window and other windows; including resizing and minimizing, handling window events (etc..)  you'll have to use Xlib. 

Xlib is very low level, while it is possible to create a GUI application with Xlib, it is very tedious and besides you'll be re-writing functionality that is provided by the GUI toolkits (GTK, QT, FLTK, wxWidgets etc) and all the GUI toolkits provide an interface to OpenGL.

I definitely would not recommend using Xlib to code a GUI.  Just coding a text input widget with Xlib is quite a bit of work, you'll have to write code for backspacing, using the delete and enter keys, handling events, you'll even have to write code to print and control the cursor character etc.

The only reason I see for using only Xlib and GLX would be if for some reason you absolutely don't want to use any other libraries.
(GLX and Xlib are installed by default on all Linux distributions)

---

### Post by thedardanius on 2012-05-25
exactly!!!
thANS FOR the info.
You need to know, my engine provides it own GUI system (input, push etc. all coded by me already using opengl). So i wish to use glx cause it is on all linux distro's etc. but is a function included in xlib for resizing, maxwidht etc??
which functions???

---

### Post by xytron on 2012-05-25
> **thedardanius said:**
> exactly!!!
thANS FOR the info.
You need to know, my engine provides it own GUI system (input, push etc. all coded by me already using opengl). So i wish to use glx cause it is on all linux distro's etc. but is a function included in xlib for resizing, maxwidht etc??
which functions???

You can try using the XiconifyWindow() function.

You should be aware that the functionality of minimizing, maximizing, setting window decorations, moving windows around on the desktop also interact with the Window Manager so this complicates things a bit.  The Window manager may not honour all such requests, it depends on the specific Window Manager being used and your application usually doesn't control that choice.

I'd also not recommend trying to program around the Window Manager.  If you create an OpenGL window with GLX that window will be handled by the Window Manager, why do you need a function to  minimize windows?  That Window Manager will provide that functionality already as well as your windows decorations.  Are you trying to disable minimize and maximize?  You can do that when you create the window.

Also when you create the window is when you set its size, when the window is resized it generates the ConfigureNotify event, you would handle anything pertinent to window resizing within that event.

You can try to force a window resize with the XResizeWindow() function, but again the Window Manager can override such a resize.

I'd recommend studying Xlib, specifically Xlib window creation and events, and depending on what you are doing also about Window Manager interaction.

---

### Post by thedardanius on 2012-05-25
I see you dont get the point:
If my engine is out of focus, the engine should resize automaticaaly (windows)
if this happens on ubuntu already, tell me. If not, how am I supposed to do this then?
Also, how can I get the real widht of a screeen, with waht functions?

---

### Post by xytron on 2012-05-25
> **thedardanius said:**
> I see you dont get the point:
If my engine is out of focus, the engine should resize automaticaaly (windows)
if this happens on ubuntu already, tell me. If not, how am I supposed to do this then?
Also, how can I get the real widht of a screeen, with waht functions?

Whenever a window is resized it generates the ConfigureNotify event, which your program will need to handle.

To get the width in pixels of the screen you can use the DisplayWidth macro provided by Xlib (there are many other such macros).

You should be able to find some Xlib tutorials online, Xlib is not so hard to learn, there are quite a few functions and macros though.

---

### Post by thedardanius on 2012-05-31
ok, so Xlib is the lib I need?
BTW, would ou recommend me to use gtk? Becuase the sound library I use (BASS) onlyhas support for gtk, i thought.... I'll ask the bass forum.

---

