---
title: "Graphics without the GUI or event-loop"
date: 2010-08-15
forum: Programming Talk
---

### Post by crampus on 2010-08-15
I am asking for help and suggestions from those with experience with various graphical sub-systems and libraries on Linux.

We are producing cross-platform code, consisting of a number of different programs, performing simulations of real-life processes. The system will have no need for any graphics once in production, but the fidelity of simulations and research into the alternatives could be judged so much better if one had a graphical view of their inputs and processes while the code is running. Thus, what we need, can perhaps best be described as a "graphical monitor" (or debugger?). The "command-line" programs that perform simulation will communicate their variables and structures by placing them in process-shared memory and passing the messages to graphical monitor requesting that a graphical representation of data in the shared memory be depicted in a window.

The graphical monitor, once initiated, has no need for user control or configuration interface or any need to respond to the events of typical GUI (keyboard, mouse, etc.) The only exception might be (if this does not complicate things by interfering with the message response protocol) re-sizing and minimizing of its window.

Further requirement for that program are:

Portability. The system will be used on many different variants of Linux. Dependency on any library not commonly found on the system is to be avoided. 

Drawing speed/efficiency. In order to respond to real-time simulation large volume of short vectors or filled polygons might have to be drawn as a response to a single message.

Binary distribution. This is an in-house project: recompiling new versions on each end-user's system is to be avoided.

Graphics. The program must show point locations with small bit-map symbols in specified colors, line segments in various line-widths and colors, filled triangles (ideally "shaded") with random and regular patterns and text labels with only a single font but preferably in various colors and sizes. The program must be able to depict on the window memory-resident .png and .jpeg images, and must be able to write out (or provide a pointer to a shared memory block of) the current bit-map of the display.
  
I am now considering either raw x(lib) or gtk2. I'll be grateful for any comments and suggestions.

crampus

---

### Post by kahumba on 2010-08-15
I think you're overreacting.
Just use Gtk with OpenGL and you're fine since OpenGL (through SDL or GLUT) is the best and fastest real-time drawing solution.
Gtk doesn't need/force you to use a keyboard etc, _you_ (the app developer) decide how the app will work - with or without a need for a keyboard, mouse etc.

---

### Post by SledgeHammer_999 on 2010-08-15
Or if you don't have access to OpenGL, I think Gtk+Cairo is the most efficient drawing API in software mode. (not from personal experience).

---

### Post by crampus on 2010-08-15
> **SledgeHammer_999 said:**
> .. Gtk+Cairo is the most efficient drawing API in software mode.

Things like Cairo (let alone OpenGL) is exactly what we don't want to depend on: we would like to deploy binaries of this program with a reasonable expectation it will have no unexpected but required run-time dependencies, no matter what Linux distribution and release level it lands on.    

We are now considering just GDK, without GTK+. It may well do all we need.

crampus

---

### Post by worseisworser on 2010-08-15
> **crampus said:**
> Things like Cairo (let alone OpenGL) is exactly what we don't want to depend on: we would like to deploy binaries of this program with a reasonable expectation it will have no unexpected but required run-time dependencies, no matter what Linux distribution and release level it lands on.

Then link statically:

[INDENT]Alternatively, static linking can be forced with the -static option to gcc to avoid the use of shared libraries:[/INDENT]
-- [http://www.network-theory.co.uk/docs/gccintro/gccintro_25.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_25.html)

---

### Post by worseisworser on 2010-08-15
A quite portable option is the HTML5 canvas: 
  [http://mrdoob.com/projects/chromeexperiments/ball_pool/](http://mrdoob.com/projects/chromeexperiments/ball_pool/)

Chrome and Firefox works everywhere, and there's a chance IE9 (which only works on Windows, but, yeah) will get proper suppert for HTML5 canvas.

It might be fast enough for what you need; it is certainly ..very.. fast here under Chrome 6.x.

---

### Post by kahumba on 2010-08-15
> **crampus said:**
> Things like Cairo (let alone OpenGL) is exactly what we don't want to depend on: we would like to deploy binaries of this program with a reasonable expectation it will have no unexpected but required run-time dependencies, no matter what Linux distribution and release level it lands on.    

We are now considering just GDK, without GTK+. It may well do all we need.

crampus
GDK as a drawing solution is crap and considered outdated, the industry and the Linux desktop in general is clearly heading for OpenGL backed solutions (even Gnome 3), but GDK may still do well for you, good luck with that.
One thing I know for sure, this is the type of project I'd certainly wish to avoid: paranoid "don't touch it" requirements while also expecting for a "real-time <insert-other-buzzwords-here> final product".

---

### Post by worseisworser on 2010-08-15
> **kahumba said:**
> GDK as a drawing solution is crap and considered outdated, the industry and the Linux desktop in general is clearly heading for OpenGL backed solutions (even Gnome 3), but GDK may still do well for you, good luck with that.
One thing I know for sure, this is the type of project I'd certainly wish to avoid: paranoid "don't touch it" requirements while also expecting for a "real-time <insert-other-buzzwords-here> final product".

Yes, he's actually looking for a dataflow/reactive framework/library so he can hook in arbitrary observers to any of his memory cells (objects; yay), but I do not think I want to talk about any even remotely interesting or useful paradigm in here again for a while.

..I'm gonna let you guys fiddle around with your nail clippers while I go move mountains with my brain. :)

---

### Post by SledgeHammer_999 on 2010-08-15
> **crampus said:**
> We are now considering just GDK, without GTK+. It may well do all we need.
crampus

In Gtk+ 3.0, gdk will use cairo. In fact, I think a couple days ago the old model was deprecated and patches landed that make use of cairo. Till now you could use the gdk+old method or gdk+cairo.

As someone said, link statically, the license permits it.

---

### Post by GenBattle on 2010-08-17
To me it sounds as if you're being too fussy. About the only way you're going to achieve the sort of platform independence you're talking about is by rendering the content/controls you want directly through OpenGL. Every library is going to have dependencies, and each distro has a different set of installed libraries.

I would imagine the only things which you could guarantee across all linux distros is X11/OpenGL, but even then, nothing is certain. If you use GTK, you're automatically dependent on the Gnome desktop environment.

Maybe go back to your client and say "Give me an exact and explicit list of the operating systems we want to support". If you can't do that, then you're setting yourself up for some misery. Your other option is to just say on your download page "this program requires <Library> ver. X.X" and make sure you use the appropriate distribution's package management system to specify dependencies (i know .deb allows you to specify dependencies which should be installed).

---

### Post by SledgeHammer_999 on 2010-08-17
> **GenBattle said:**
> If you use GTK, you're automatically dependent on the Gnome desktop environment.

That's not true. Stop spreading these lies.

---

### Post by crampus on 2010-08-17
> **GenBattle said:**
> Maybe go back to your client and say "Give me an exact and explicit list of the operating systems we want to support". If you can't do that, then you're setting yourself up for some misery. Your other option is to just say on your download page "this program requires <Library> ver. X.X" and make sure you use the appropriate distribution's package management system to specify dependencies.

If I tell the client they have to keep managing distribution packages for different Linux distros as these are coming and going, as long as the software is in use, I know exactly what will happen: they will say "9 out of 10 among the engineers that would benefit from the graphical view into the simulation they are fine-tuning use MS Windows. Let's forget about Linux support...". This is an in-house project (although in a large, geographically diverse organization); the user base is perhaps a hundred, or, optimistically, a couple of hundreds - certainly not in the thousands. They are willing to give some of their user a choice because these are experts in their fiels and in some locations Linux is actually gaining acceptance, but they are not willing to give up "binary distribution, Windows style". I can certainly see the numbers forcing them to take this position. 

crampus

---

### Post by GenBattle on 2010-08-17
> **SledgeHammer_999 said:**
> That's not true. Stop spreading these lies.

Right you are, my bad.

Binary support on windows is no more straightforward than binary support on GNU/Linux (replace libraries with DLLs, e.g. msvc runtimes). The difference is that with windows you're talking about one operating system versus potentially hundreds of different operating systems that constitute GNU/Linux.

If i were doing such a project (and source release wasn't possible), i would focus on a few main operating systems/platforms your end users will be using and compile/optimize/package for those (e.g. Ubuntu, Debian, Fedora, Suse); this is the approach most GNU/Linux software projects take, along with source distribution (e.g. firefox). Most likely this sort of finite set would catch 80%+ of your non-windows users (but i know about as much about distro market share as i do about GTK dependencies :p).

For a user base of a couple hundred people, you don't want to be jumping through the hoops of trying to put the software on everyone's preferred platform.

This is just my opinion though, and i am no more than a humble junior developer, fresh out of uni, not to mention a complete newb of an Ubuntu developer.

---

