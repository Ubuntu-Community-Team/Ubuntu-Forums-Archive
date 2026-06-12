---
title: "C++ and OpenGL?"
date: 2006-03-04
forum: Programming Talk
---

### Post by OakRand on 2006-03-04
This is not related to Ubuntu, but I have found the knowledge on this forum to be very good so I thought I'd ask my question here.

I am looking to develop a graphical program for manipulating 3D models of proteins. The data files are essentially just giant matrices of dimensions nx3.  Currently there's nothing out there that does what I need, although if you're really interested there is a program called Pymol which is along the lines of what I would like.

I'm a C programmer and so naturally was thinking of using C++. I know very little about creating gui's other that what I learned over a short period working with Java four years ago.

I think C++ with OpenGl is the best route but would like to hear anyone else's input, particuarlly about how to get started (books, websites, etc).

Thanks.

---

### Post by hod139 on 2006-03-05
If all you want nice visualization check out [VTK]("http://public.kitware.com/VTK/") (there's even a ubuntu package in the repos).  Also a quick google search found [this page]("http://garlic.mefos.hr/garlic/competition/index.html") for free molecular visualization programs.

If you really want to build something yourself, check out [SDL]("http://www.libsdl.org/index.php"), and [Open Scene Graph]("http://www.openscenegraph.org/").

For an OpenGL tutorial, the "Red Book" is considered the definitive guide.  Version 1.4 is the newest, but you can view [version 1.0 online]("http://www.opengl.org/documentation/red_book_1.0/") for free.

---

### Post by OakRand on 2006-03-05
Thanks for the links. OpenSceneGraph looks quite interesting.

I'm familiar with the majority of molecular viewing programs out there. The problem is I need something to display the results from a program I've written, and regardless of which visualization program I use it involves a lot of scripting and the end result is only satisfactory.

---

