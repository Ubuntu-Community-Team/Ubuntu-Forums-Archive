---
title: "Trying OpenGL for Uni, weird xwindow output."
date: 2010-11-04
forum: Programming Talk
---

### Post by Devio on 2010-11-04
Hi, for a module at uni we're learning the basics of openGl programming and I'm yet to even get started properly as I cant for the life of me figure out what's wrong with the output...

The code compiles, everything seems fine then I go to run it and the Xwindow pops up and it looks all artifacted, I can close and run it again a few times and it will change slightly too.  I have the packages we needed such as libglut3, libglut3-dev, libxmu6 and libxmu-dev.

I'm using a makefile to compile the examples which I had to edit due to one of the extensions on the compile code was -lXi which I didn't have, I'm kinda suspecting that might be contributing to the problem but I don't have a clue where I'd find the package.

I'm closer doing this on my own machine with these errors, there's no way of running the examples on the campus computers until a rebuild of the student profile next semester. However, I'm still struggling since I'm a bit of a newbie to Linux and it would only be harder making the program in Windows.

I guess what I'm asking is, am I right in thinking I need the package for -lXi and if so where do I get it?  Otherwise what else could be causing weird problems in the windows openGL brings up?

Oh and sorry if this is in the wrong section, it's about C programming kinda so that's why I posted here.

Thanks for reading, hope I've made sense.

---

### Post by Zugzwang on 2010-11-04
Did you try turning off the desktop effects, i.e., using a window manager different that compiz?

---

### Post by Devio on 2010-11-04
It seems that it really was that simple, I just turned the visual effects off and it seems to be fixed!  Thanks so much! Sorry I never even thought of that!

Cheers! You've saved my assignment I think!

---

