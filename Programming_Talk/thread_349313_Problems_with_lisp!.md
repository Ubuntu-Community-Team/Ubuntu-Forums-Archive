---
title: "Problems with lisp!"
date: 2007-01-30
forum: Programming Talk
---

### Post by Wybiral on 2007-01-30
Hello, I've been on/off playing with lisp for a while (GNU Common Lisp) and I'm curious about something... Everything I've done so far has been simple non-library based stuff, mostly command line experimentation. So, being the OpenGL fan that I am, I decided to look for an OpenGL library for it... I found one! cl-sdl and cl-sdl-opengl (from synaptic)

So I've been trying to get them to work, I even found a bunch of examples... But I keep getting told that SDL and GL doesn't exist!

I can't seem to find any tutorials on using libraries with lisp or any kind of linking or anything... I have no idea what I'm doing.

If anyone might know how to get this cl-sdl-opengl library working with my "gcl" that would be great!

Thanks.

Also any general advice on linking/compiling lisp program would be appreciated.

---

### Post by jblebrun on 2007-01-30
> **Wybiral said:**
> Hello, I've been on/off playing with lisp for a while (GNU Common Lisp) and I'm curious about something... Everything I've done so far has been simple non-library based stuff, mostly command line experimentation. So, being the OpenGL fan that I am, I decided to look for an OpenGL library for it... I found one! cl-sdl and cl-sdl-opengl (from synaptic)

So I've been trying to get them to work, I even found a bunch of examples... But I keep getting told that SDL and GL doesn't exist!

I can't seem to find any tutorials on using libraries with lisp or any kind of linking or anything... I have no idea what I'm doing.

If anyone might know how to get this cl-sdl-opengl library working with my "gcl" that would be great!

Thanks.

Also any general advice on linking/compiling lisp program would be appreciated.

Have you been using Practical Common Lisp as a reference? 
[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)

It has a chapter on packages, which i think will help you:
[http://www.gigamonkeys.com/book/programming-in-the-large-packages-and-symbols.html](http://www.gigamonkeys.com/book/programming-in-the-large-packages-and-symbols.html)

I haven't gotten that far yet, so I'm not sure if it's what you want. Just thought I'd throw it out there.


EDIT:

Look in /usr/share/doc/cl-sdl

---

### Post by jblebrun on 2007-01-30
Wow, ok, nevermind, I see what you mean... none of the cl-sdl-demos work, nothing in the docs works... 

I bet Inostodal will have the answer!

---

### Post by lnostdal on 2007-01-30
the libraries and stuff in the ubuntu repos lag too much.. i never use them so i know nothing about them .. (edit: oh; and i'm using a recent > 1.0 cvs version of SBCL also .. not GCL).. instead of showing how to install sdl i'm going for cl-opengl because i've recently installed that one and i'm lazy

i'm using the version here: [http://common-lisp.net/project/cl-opengl/](http://common-lisp.net/project/cl-opengl/) .. download it and create a symlink to it so asdf/sbcl can find it:

```
lars@ibmr52:~/programming/lisp$ darcs get http://www.common-lisp.net/project/cl-opengl/darcs/cl-opengl/
lars@ibmr52:~/programming/lisp$ ln -s /home/lars/programming/lisp/cl-opengl/cl-opengl.asd /home/lars/.sbcl/systems/

```

the repo also contains other asd-files (for glu and glut) which we also symlink in the same way

looking in the asd-file i see that cl-opengl depends on cffi .. i've installed that too in the same manner.. alt-tabbing to emacs/slime i now type (require :cl-glut-examples) and it starts compiling all the libraries (both cffi, cl-opengl, cl-glu and cl-glut) since they are dependencies of the requested cl-glut-examples

i can now type (cl-glut-examples:gears) and a version of the standard opengl-gear demo (written in lisp) pops up:

[IMG]http://nostdal.org/~lars/cl-opengl.png[/IMG]

.. arrow-keys rotate it by x and y axis .. and z and Z rotates by z-axis..

---

### Post by Wybiral on 2007-01-30
Thanks lnostdal, I'll check that one out.

But no one can get cl-sdl, cl-sdl-image, and cl-sdl-opengl to work?

SDL is really what I need because it has better event handling and sdl-image which I'll need for textures and stuff.

I want to write some good 3d game demo's in lisp because I think it original (I haven't seen to many of them) but I'm really going to need to get this cl-sdl thing working.

But, thanks for the glut example, I'll definitely check it out too.

---

### Post by Alasdair on 2007-01-30
I'm using SBCL, but assuming you installed all the cl-sdl stuff from the ubuntu repos, all you need to do is:
```

(require :sdl)

```
you can also load the sdl-demos package, and then run the commands:
```

(require :sdl-demos)
(sdl-test:start)

```
And you should get a window as shown (see attached). I'm not even sure if cl-sdl even works with GCL (CLiki doesn't show it on the list of supported implementations) you might want to try a different lisp implementation such as SBCL if that doesn't work.

---

### Post by Wybiral on 2007-01-30
> **Alasdair said:**
> I'm using SBCL, but assuming you installed all the cl-sdl stuff from the ubuntu repos, all you need to do is:
```

(require :sdl)

```
you can also load the sdl-demos package, and then run the commands:
```

(require :sdl-demos)
(sdl-test:start)

```
And you should get a window as shown (see attached). I'm not even sure if cl-sdl even works with GCL (CLiki doesn't show it on the list of supported implementations) you might want to try a different lisp implementation such as SBCL if that doesn't work.

Wow, thanks... That worked. Unfortunately it didn't work with gcl, so I went ahead and got sbcl... But anyway, I got the examples running, thanks again.

---

