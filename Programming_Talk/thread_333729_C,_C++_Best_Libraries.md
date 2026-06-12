---
title: "C, C++ Best Libraries"
date: 2007-01-07
forum: Programming Talk
---

### Post by phossal on 2007-01-07
First, I'm a fan of any language that solves the problem at hand in the shortest, easiest, most readable way. Sometimes though, we have to *resort* to C and C++. 

What are the *very best* non-standard libraries freely available for C or C++, and why? Relate your experience, and any tips.

---

### Post by Mirrorball on 2007-01-07
Boost. It's a collection of libraries. I have already used the unit testing suite, a mathematical function that saved my life (sinc), and Boost Python for using C++ with Python. Blitz++ must be awesome for numerical computing, but I never had a chance to test it.

---

### Post by Grey on 2007-01-07
I think that really depends on what you are going to be using the language for.  My line of work (console development), pretty much means that I write everything from scratch.  Even a good chunk of the STL.  

But personally, the only libraries I've really spent a lot of time with are SDL (pretty nice), libao (good, if you only want simple sound.  You have to write your own threading if you want something fancier), pthreads (VERY nice), libmad (FANTASTIC MP3 decoding), libvorbis (again, fantastic), and GTK+ (ugly.  But pretty nice once you get the hang of it.  You might prefer GTKMM, but I haven't used it).

---

### Post by Wybiral on 2007-01-07
Whew... SDL and GLUT for OpenGL applications (OpenGL is one of my main addictions)... SDL is less restrictive and compiles to be a little more bloated, while GLUT is more restrictive (by taking control of program flow through a main loop) but is able to produce much smaller compile sizes. So it depends on the purpose and size of the OpenGL program you want to write.

SDL also offers an amazing library known as SDL_image that allows you to easily load images for use as OpenGL textures (from bmps to pngs...)

I've messed with boost's python binding as mentioned by Mirrorball, but I've personally found that simply using the python development files (python.h) to be just as easy with much less overhead (and much like boost, capable of providing two way communication between compiled C/C++ programs and external (or embedded) python scripts).

Those are the most common libraries I use, for everything else that I do, there seems to be enough in the STL and if not, I can usually implement it myself (in the time that it would take to fully learn a new library)

---

