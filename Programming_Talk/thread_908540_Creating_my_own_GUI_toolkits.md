---
title: "Creating my own GUI toolkits"
date: 2008-09-02
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-09-02
You always hear debates on the functionality and whatnot of KDE vs GNOME. Respectively, each of these desktop environments USUALLY use either the qt GUI toolkit, or the GTK GUI toolkit. Then you go on to think about how Windows has it's own way of making GUI's, along with the Mac OS.

So let's say I was this crazy guy with lots of time on my hands who wasn't satisfied with any existing toolkits used to create GUI's with. Let's say that I would rather have MY applications be linked with a GUI frontend coming from all of my own coding. My very own creation that I could use on all my application, to give their interfaces their own unique feel. Now, I've already thought of a lot of stuff, such as how my application wouldn't 'fit in' with the others on <X> desktop OS. But then, let's say that I've written my own operating system, and I want all my stuff to look one way and not the other; similar to how the Mac OS runs their rig. 

What kind of work goes into creating such libraries? How advanced would one's programming skills have to be in order to complete such a task? How long might it take for a programmer with skill level <X> to do this? Would the programmer have to do something special to make her GUI library work on existing interfaces, like the X window system? Or is the point of interfaces like X to conform to other programmers code?

Before I go on too long, I'm sure you see where I'm going with this and what I mean.

This is simply a curiosity. I have no immediate intention of starting such a project, only desire to know if I could or not (at a reasonable level, of course).

---

### Post by LaRoza on 2008-09-02
Most of the Linux toolkits work on top of an implementation of X (not all do, but GTK+ and QT do)

So you'd have to write a framework either from the ground up, or write it to run on X.

Exactly what goes into it, I don't know.

It would depend on the complexity desired. Writing an extremely simple GUI toolkit probably wouldn't be all that hard, but it wouldn't be all that useful either.

---

### Post by WW on 2008-09-02
One of the smallest usable GUI toolkits is [FLTK](http://www.fltk.org/) (the "Fast, Light Toolkit").  You might be able to answer your own question by browsing through its source code.  You could also get the source for GTK+ or Qt, but FLTK is a smaller library, so it would probably be a better library to get a feel for a lower bound on the effort required.

---

### Post by Sinkingships7 on 2008-09-02
Well, pending that I don't get anymore replies to my original question, let's turn this into a small debate. What is your favorite GUI toolkit (if any) any why? If you do not have a favorite, please state some of the pros and cons of various toolkits you have used.

---

### Post by mssever on 2008-09-02
> **Sinkingships7 said:**
> Well, pending that I don't get anymore replies to my original question, let's turn this into a small debate. What is your favorite GUI toolkit (if any) any why? If you do not have a favorite, please state some of the pros and cons of various toolkits you have used.
Yay, a new flamewar! :popcorn:

The only toolkits I've written for are GTK and WX (specifically the Python bindings for both). Of the two, I've had an easier time with GTK.

I have a strong dislike for Tk, because I believe that a GUI toolkit should follow native look and feel. GTK and Qt both get passes on this since one or the other tends to define native L&F. But Tk is just plain ugly. And even though there has been some effort to make it look better, the Linux port is still ugly and doesn't follow the system theme.

---

### Post by snova on 2008-09-02
I like Qt, because it's written in C++ and is neatly organized as classes.

GTK looks weird under KDE, but maybe that's just in comparison with all the Qt-based windows surrounding it.

Here's an idea: make a GUI toolkit with a state-based API, like OpenGL. Something like this would be neat:

[php]guiBeginLayout( LAYOUT_VERTICAL );
guiAddPushButton( "Hello, World!", OnButtonClick );
guiEndLayout();[/php]I thought of that a while back, but put it out of my head.

> Most of the Linux toolkits work on top of an implementation of X (not all do, but GTK+ and QT do)How else can you do it? I thought the screen was managed by X; you can't go around it without talking to drivers- and that's probably not easy.

Unless, of course, you are talking about replacing all of X. Well, it might be worthwhile, but before you do, get the input of some graphics card vendors, since they'll know all about this stuff. I mean, who better to design a graphics API than a company specializing in such things? I don't mean drivers, I mean the architecture of the X server.

And while you're at it, replace some other system components like this, by getting input from the manufacturers.

---

### Post by techmarks on 2008-09-02
With some determination I'm sure you could create a new GUI toolkit.  It seems very time consuming.  You'll probably want to learn Xlib fairly well, and Xlib documentation is not so great, it's mostly scattered all over the web, and some of the older books from O'Reilly.  

I think it might also be possible to use some Xlib and Cairo to create windows and such, but more experimenting about this is needed, I don't know.

I like FLTK alot it's simple, good documentation, OpenGL with it is super easy, I'm having some issues with the mouse programming of it, but I'm still hoping to resolve it.

Also GTK+ is great, well designed, a little messy with OpenGL, 
lots of widgets, my only issue is that it's in C, I know that the great portability of it is because of that and in the end it's very good, but if you want to use GTK+ with some of the existing C++ libraries sometimes that gets messy.

I've only tried those two, of course there's Xlib, but it's too bad the documentation is very lacking.

p.s.  forgot about wxwidgets I only tried it on Windows and it was well ok,  the exes it produced are HUGE, documentation not always very clear.

---

### Post by jespdj on 2008-09-03
[Comparison Of Linux GUI Toolkits - Which one Do you Want ?](http://www.thecredence.com/comparison-of-linux-gui-toolkits-which-one-do-you-want/)

[Choose Your GUI Toolkit](http://www.awaretek.com/toolkits.html)

---

