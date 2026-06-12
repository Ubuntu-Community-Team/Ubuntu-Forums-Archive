---
title: "Compilation for beginners"
date: 2006-05-30
forum: Programming Talk
---

### Post by walkingbeard on 2006-05-30
I've being programming tiny bits and bobs for absolutely ages - ten years or so.  And I still don't know anything about compilation.  If you read a tutorial on doing this, or doing that, in C or C++, they always, always forget to tell you about compiling it, like it's an obvious step.  It's not.

I'm just fed up with IDEs.  The only one that has ever worked how it should, is Visual Studio, which isn't really a viable option with Linux, to say the least.

Can anyone point me in the direction of a really basic introduction to compiling things?  Where they explain how to compile lots of source files together, from the command line.  And (since I'm using SDL to do some graphics work), what also these bizarre parameters, like -dSDL and things like that mean.

Then I want to find out about makefiles and configure scripts and stuff.  I want to make my own, so I can understand what all that nonsense is when you build a source package you've downloaded.

---

### Post by Sef on 2006-05-30
First to compile, download build-essential

sudo apt-get update

sudo aptitude install build-essential

Second, read this tutorial on   [installing]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by walkingbeard on 2006-05-30
Thank you, but this isn't what I meant.  I want to know how to compile things.  Completely.  I want to compile my programme and link it and know what is going on at each stage.

---

### Post by moberry on 2006-05-30
I would go to a site like developer.gnome.org and read there howtos on making makefiles, etc. A GREAT resource I have is a book called "Linux Programming in 24 hours" it has a whole chapter on making makefiles, etc.

---

### Post by moberry on 2006-05-30
That link will do you just right. For help on linking libraries like GTK, etc read the documentation for pkg-config.

[http://users.actcom.co.il/~choo/lupg/tutorials/writing-makefiles/writing-makefiles.html](http://users.actcom.co.il/~choo/lupg/tutorials/writing-makefiles/writing-makefiles.html)

---

### Post by lnostdal on 2006-05-31
check out the free book, "An Introduction to GCC": [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/)

---

### Post by Joetheodd on 2006-05-31
[QUOTE=walkingbeard]I've being programming tiny bits and bobs for absolutely ages - ten years or so.  And I still don't know anything about compilation.  If you read a tutorial on doing this, or doing that, in C or C++, they always, always forget to tell you about compiling it, like it's an obvious step.  It's not.

I'm just fed up with IDEs.  The only one that has ever worked how it should, is Visual Studio, which isn't really a viable option with Linux, to say the least.

Can anyone point me in the direction of a really basic introduction to compiling things?  Where they explain how to compile lots of source files together, from the command line.  And (since I'm using SDL to do some graphics work), what also these bizarre parameters, like -dSDL and things like that mean.

Then I want to find out about makefiles and configure scripts and stuff.  I want to make my own, so I can understand what all that nonsense is when you build a source package you've downloaded.[/QUOTE]


Say you have a small source file, someprogram.c, and you want it compiled.

$ gcc -o someprogram someprogram.c
$ ./someprogram

and your program has been run. Attach extra .c files to the end of the gcc command to add extra files.

---

### Post by garba on 2006-05-31
[QUOTE=Joetheodd]Say you have a small source file, someprogram.c, and you want it compiled.

$ gcc -o someprogram someprogram.c
$ ./someprogram

and your program has been run. Attach extra .c files to the end of the gcc command to add extra files.[/QUOTE]

this is one deep insight, it's clear he's just getting started hence he's not ready yet for topics as advanced as these :rolleyes:

---

### Post by moberry on 2006-06-01
[QUOTE=garba]this is one deep insight, it's clear he's just getting started hence he's not ready yet for topics as advanced as these :rolleyes:[/QUOTE]

Makefiles are hardly deep insight. It is a good idea to go ahead and get into the practice of using them.

---

### Post by garba on 2006-06-01
[QUOTE=moberry]Makefiles are hardly deep insight. It is a good idea to go ahead and get into the practice of using them.[/QUOTE]

not a fan of sarcasm aren't you? too bad :mrgreen:

---

