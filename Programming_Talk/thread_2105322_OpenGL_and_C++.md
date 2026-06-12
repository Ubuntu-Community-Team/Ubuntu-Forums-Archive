---
title: "OpenGL and C++"
date: 2013-01-15
forum: Programming Talk
---

### Post by mustafa1990 on 2013-01-15
Hi.

How do I implement the OpenGL for C++ on Geany or Eclipse.. I dont know what to install from Synaptics. I found something called freeglut3 but.. what should I do.

I would like to use the OpenGL on Eclipse or Geany GUI, it is possible?

---

### Post by MG&amp;TL on 2013-01-15
<advice>

Do you know C++ very well? No disrespect, but from what you're saying, it doesn't sound like you are. (I'm in the same boat...) If that's the case, then I suggest laying off the OpenGL for a while, and learning C++ for a while. Not being comfortable with C++ is just (one extra) pain in the rear while learning OGL.

</advice>

Anyway, to write an OpenGL application on linux, you'll need three things to get started:

1. OpenGL itself. You'll want the *libgl1-mesa-dev* package.

2. A windowing library. This could be X11, but I'd recommend freeglut (*freeglut3-dev) *or GLFW (*libglfw-dev*), as X11/GLX has some peculiar gotchas.

3. An OGL extension library. While not strictly necessary, if you want to use anything other than core OpenGL, you'll want an extension loader/information library to abstract the actual implementation of the extensions. The de facto standard for this on linux appears to be GLEW, which comes in the package *libglew-dev*.

As for IDEs, sorry, can't help with those. Normally, you'll add the extra flags required into the build commands entry.

G'luck (you'll need it!).

---

### Post by mustafa1990 on 2013-01-15
Thanks for helping me, I am just an student. I am taking a course of C++ and Computer graphics

---

### Post by MG&amp;TL on 2013-01-16
> **mustafa1990 said:**
> Thanks for helping me, I am just an student. I am taking a course of C++ and Computer graphics

Ah. Well, in which case, I suggest the arcsynthesis tutorials: [http://arcsynthesis.org/gltut/](http://arcsynthesis.org/gltut/)

---

### Post by PaulM1985 on 2013-01-16
I used this when I was getting myself set up for C++ and OpenGL dev.  
[http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/home.php](http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/home.php)
I find videos can be more helpful.  Hopefully the set up videos are still in date.  I have used the others more recently and the way they do stuff still applies.

Good luck with it

Paul

---

### Post by mustafa1990 on 2013-01-19
Thank you very much all of you!! Thank you for all the information you are giving me friends! 

May I recommend a website for you guys, if you are interested
[http://ocw.mit.edu/index.htm](http://ocw.mit.edu/index.htm)

---

