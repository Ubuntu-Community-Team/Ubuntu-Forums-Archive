---
title: "IDEA: Embedding a window in web browser"
date: 2008-01-25
forum: Programming Talk
---

### Post by Aerin on 2008-01-25
Hi, 

I was reading the howto on having a terminal window as the desktop background, ([http://ubuntuforums.org/showthread.php?t=202249]("http://ubuntuforums.org/showthread.php?t=202249")) when I thought about this. It involves having some code written in c++(or lua, or python etc) (say using sdl and opengl) embedded in a web page.  A firefox/epiphany plugin would read the code, create an empty box in the web page where the window is supposed to be (much like java applets do). Then it would invoke another application to open a borderless window which does not show up in the taskbar just where the empty box was created - making it appear that the window is embedded in that page. The plugin would somehow change the position of the window and resize it, clip the viewport as necessary, when the page is scrolled.

Then maybe we can have open source hardware accelerated 3d graphics in a web browser! There may be a need for a nice framework (a 2d/3d engine) of which there are plenty out there, with an easy to learn lua scripting interface or something. But is this thing feasable? Has this already been attempted?

---

### Post by LaRoza on 2008-01-25
I don't understand.

Do you mean like Opera widgets (which you describe very well), Java Applets or Tclets, or Flash videos?

You are describing Flash videos and Applets to a point. (An external app, written in another language, embedded in a browser)

For security reasons, almost all browsers (IE excepting) don't allow access to the system.

---

### Post by Aerin on 2008-01-25
I meant something like java applets. But in c++, using sdl and opengl. There could be some code embedded like: open a 200x300 window, paint it black, make a blue square. The code is passed to an already running process in the background, which opens an sdl window without borders in the specified place. Which carries out the functions described in the web page. It is not actually embedded, but a kind of fake embedding. 

It is something like downloading a script, and opening it using the 'framework', which reads the instructions and carries it out. 

Is there not a way to communicate between the browser and another running application? It would just display graphics, not do anything like save files, open files for security reasons. Sorry if I'm not able to explain it. I know very less about these things.

---

### Post by LaRoza on 2008-01-25
> **Aerin said:**
> I meant something like java applets. But in c++, using sdl and opengl. There could be some code embedded like: open a 200x300 window, paint it black, make a blue square. The code is passed to an already running process in the background, which opens an sdl window without borders in the specified place. Which carries out the functions described in the web page. It is not actually embedded, but a kind of fake embedding. 

Is there not a way to communicate between the browser and another running application? It would just display graphics, not do anything like save files, open files for security reasons. Sorry if I'm not able to explain it. I know very less about these things.

Why? The only languages that I know that allow such things are Java, Tcl, and Jython.

Why C++? That wouldn't work at all. Java, Tcl and Jython run in a virtual machine and can be run, without altering, on any OS with the VM installed.

C++ is compiled to binary code, which is not portable. It goes against logic.

One could let a browser do what you describe, but no sane browser would allow it.

---

### Post by Aerin on 2008-01-25
> **LaRoza said:**
> Why C++? That wouldn't work at all. Java, Tcl and Jython run in a virtual machine and can be run, without altering, on any OS with the VM installed.
Oops. I wasn't thinking. :| You are right, it wouldnt work that way. I'm now thinking about only the graphics rendering having abandoned the idea of opening _any_ window that the programmer wants to. 

I'm thinking about a framework. that can interpret code written in lua. The framework will have separate binaries for different platforms, but the lua code will be the same for all platforms. There will be only a few functions related to graphics rendering to prevent security exploits. 

The idea of the browser allowing direct access to the system is bad. There will be only scripts, not binary code embedded in the page. The commands should be interpreted and very limited. There should be only functions like paint on the viewport, draw primitives, exit etc. 

What I'm driving at is the way epiphany opens some filetypes in other programs. It could open those scripts using the framework, which will parse the script and render something after opening a new window. 

The browser not allowing it is a problem though. Goodbye, idea. :(

EDIT: After a lot of googling I ran across this project - [Emma3d]("http://emma3d.sourceforge.net/"). It aims to do a similar thing. It appears to be dead though.

---

### Post by ynef on 2008-01-25
I think you just invented ActiveX, actually. We all know how well that turned out. ;-)

---

