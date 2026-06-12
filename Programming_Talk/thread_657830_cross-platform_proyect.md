---
title: "cross-platform proyect"
date: 2008-01-04
forum: Programming Talk
---

### Post by light-angel on 2008-01-04
hi
i want to create a cross-platform  proyect called ANM, basicly it will access databases, play videos, music and have a photo gallery.

the thing i wanna know is if there is a IDE like Visual Basic that can help me with that.

i know java is a good way to do it but i really don't like the fact of making all the control my program uses.

i also know C so it could be if there was a GUI designer or something like that.

i really dont care wich platform is it, since i use the 3 of them at home so it does't have to be only on Linux.

---

### Post by CptPicard on 2008-01-04
[IMG]http://icanhascheezburger.files.wordpress.com/2007/08/skeptical-cat-is-fraught-with-skepticism.jpg[/IMG]

---

### Post by lisati on 2008-01-04
> **light-angel said:**
> hi
i want to create a cross-platform  proyect called ANM, basicly it will access databases, play videos, music and have a photo gallery.

the thing i wanna know is if there is a IDE like Visual Basic that can help me with that.

i know java is a good way to do it but i really don't like the fact of making all the control my program uses.

i also know C so it could be if there was a GUI designer or something like that.

i really dont care wich platform is it, since i use the 3 of them at home so it does't have to be only on Linux.

I haven't actually tried it yet, but you might want to check out [http://www.gtk.org/](http://www.gtk.org/)

---

### Post by EXCiD3 on 2008-01-04
I would recommend Qt for this project. Its definitely much better than GTK as you can use it for many more platform abstracted operations such as saving settings (saves to registry if windows, text files in linux, etc). It works great with C/C++ and has a GUI designer that you can use.

I have used it on my own personal projects with Eclipse. Excellent choice for anyone wanting a cross platform GUI.

---

### Post by rufius on 2008-01-04
You could also go the Mono route, the IDE being Mono Develop. C# isn't a particularly hard language to learn if you can grasp Java. Mono will for sure run on Windows & Linux and I'm pretty sure Mac OS X is working as well.

Hope that helps. :)

---

### Post by pmasiar on 2008-01-04
> **light-angel said:**
> hi
i want to create a cross-platform  proyect called ANM, basicly it will access databases, play videos, music and have a photo gallery.
.

There is about a thousand existing projects doing just that, why you don't join one of them instead of creating  yet another failing one?

---

### Post by emperon on 2008-01-05
wxwidgets, java and mono gives you cross platform choices for guis. my recommendation would be make core cross platform and write seperate guis fo all platforms. I would go with mono but that's me

---

