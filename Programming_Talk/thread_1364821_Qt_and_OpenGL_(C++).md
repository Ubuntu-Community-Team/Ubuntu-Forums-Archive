---
title: "Qt and OpenGL (C++)"
date: 2009-12-26
forum: Programming Talk
---

### Post by Saxcore on 2009-12-26
Hi there. I'm currently attempting to use Qt for the first time, so I'm sure this is a fairly straight-forward question... However, I consider myself pretty poor at this programming business, so you'll have to bear with me!

I have been working on an OpenGL application, using SDL to create the buffer space, window etc. However, realising the limits of SDL ( I'd like to create a bit of a GUI), I'm going to move my application over to Qt.

I've got my head around compiling stand-alone Qt applications with qmake, however I am now unsure how to compile for Qt using the large scons file I've been adding to over the development of my OpenGL application, and not using the make file.

For now, I'm ignoring the fact that I haven't a clue how to create OpenGL buffer space on a Qt window ..  although I'm sure I'll be back here once I reach that hurdle! For now, I'm just trying to open a separate Qt window along side the SDL window of the main program, within the same program.

At the moment I'm getting an undefined reference to anything called within Qt. I'm using qmake to automate the creation of the ".pro" file, although I wouldn't have thought this would be needed. I have added all possible flags to the scons file, as well as all of the correct linking (I think!). I was just wondering if anyone could give me any pointers?

Edit: ...sorry, I've just read that post back. ...It's been a long day. I hope that makes sense. :)

---

### Post by quip on 2009-12-26
> **Saxcore said:**
> Hi there. I'm currently attempting to use Qt for the first time, so I'm sure this is a fairly straight-forward question... However, I consider myself pretty poor at this programming business, so you'll have to bear with me!

I have been working on an OpenGL application, using SDL to create the buffer space, window etc. However, realising the limits of SDL ( I'd like to create a bit of a GUI), I'm going to move my application over to Qt.

I've got my head around compiling stand-alone Qt applications with qmake, however I am now unsure how to compile for Qt using the large scons file I've been adding to over the development of my OpenGL application, and not using the make file.

For now, I'm ignoring the fact that I haven't a clue how to create OpenGL buffer space on a Qt window ..  although I'm sure I'll be back here once I reach that hurdle! For now, I'm just trying to open a separate Qt window along side the SDL window of the main program, within the same program.

At the moment I'm getting an undefined reference to anything called within Qt. I'm using qmake to automate the creation of the ".pro" file, although I wouldn't have thought this would be needed. I have added all possible flags to the scons file, as well as all of the correct linking (I think!). I was just wondering if anyone could give me any pointers?

Edit: ...sorry, I've just read that post back. ...It's been a long day. I hope that makes sense. :)

Well, as you probably guessed, undefined references mean that your calls from within Qt are not known, which means that you did not properly include the necessary libraries in your Qt files.

I have _minimal_ OpenGL experience, and less for Qt, but from the way your post reads, it sounds as though you are trying to call Qt from your OpenGL code.  If this is true, then I would think you have it backwards (again, take it FWIW since I don't have much experience in this area).  I would think the proper process would be to start a Qt application and include OpenGL libs from it, so that the drawing routines, etc., that Qt calls will be passed to or made with knowledge of the OpenGL libraries.

When I did some OpenGL programming for a Computer Graphics class (I later dropped), we used the native widgets on the machine by writing a C source file that pulled in OpenGL libs from include directives at the top; I would think this is the approach you need to take.

---

### Post by Saxcore on 2009-12-26
Hi quip, thanks for the reply. Yeah, it makes more sense to create Qt code, and then call the OpenGL libraries (although I am completely unsure of the implementation). However, for the purpose of testing them, I'm keeping them separate for the time being. So essentially my application works exactly the same as it always has, except a tiny Qt "hello world" program has been merged with it. I would have thought that (at least, in theory) the Qt code would just run when it was called, opening it's own window.

But you do have a good point. I guess I should just move my OpenGL code to a Qt program; I'm going to have to do this at some point anyway, so I may as well do it now.

..Would you know of any good resources on this matter? ..OpenGL within Qt *is* covered in the Qt help pages, except it seems extremely brief, and I'm actually having real trouble finding anything explaining the fundamentals of it on the internet. I'm using Qt designer, and am unsure if I should literally have the widgets in there to drag and drop?

---

