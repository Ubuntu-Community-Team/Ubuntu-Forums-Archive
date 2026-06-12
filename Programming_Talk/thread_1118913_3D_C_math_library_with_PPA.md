---
title: "3D C math library with PPA"
date: 2009-04-07
forum: Programming Talk
---

### Post by Kazade on 2009-04-07
Hi everyone,

Just a mini announcement really. A friend and I have been working on a simple, OpenGL-like 3D math library written in C for a while now, and I've successfully packaged it for Jaunty and uploaded it to our PPA. You can find it here: [https://launchpad.net/~kazmath-developers/+archive/ppa](https://launchpad.net/~kazmath-developers/+archive/ppa)

It's called Kazmath. If OpenGL/3D graphics is your thing, could you give it a try and let me know how you get on. The API is pretty simple, just take a look at the includes in /usr/include/kazmath 

This is kind of an offshoot of a larger project called LucadeStudios (which is on launchpad). Myself and a few friends are attempting to write a few small games while developing reusable components (Lucade stuff is C++ rather than C)

I'm currently working on another C library called Kazmodel, which will provide MD2, MD3 and OBJ model loading and animation. When it's ready it'll appear alongside Kazmath in the PPA. My friend Carsten is also working on C++ bindings for Kazmath called kazmathxx. 

Links:

Some slightly dated documentation is here: [http://www.kazade.co.uk/kazmath/docs/](http://www.kazade.co.uk/kazmath/docs/) (click the functions beginning with 'v' or 'm' for the interesting stuff - vectors and matrices)

Launchpad entry: [https://launchpad.net/kazmath](https://launchpad.net/kazmath)

---

