---
title: "Kdevelop and Linker Options"
date: 2010-05-07
forum: Programming Talk
---

### Post by scu-ba-de-buntu on 2010-05-07
I want to use KDevelop to do the following:

g++ -o"%e" ./%e.o -L/usr/lib -lalleg-4.2.2 -lm -lXxf86vm -lXcursor -lXpm -lXext -lX11 -lpthread -ldl


is that possible and how?

---

### Post by scu-ba-de-buntu on 2010-05-10
With 53 views and no ideas, I deem it impossible (or to at least unknown on this forum) to use KDevelop as an IDE for C programming with allegro.

I will be using Code::Blocks instead. Thanks anyway.

---

### Post by Zugzwang on 2010-05-11
I guess the point was that KDevelop supports different "building frameworks" (Custom Makefile, QMake, CMake, autotools, etc.), and the answer depends on which one you've used. Additionally, there's a huge difference between the versions, so in fact nobody knew for sure which are the counter-questions to be raised to you for getting your problem solved.

Also see [this thread]("http://ubuntuforums.org/showthread.php?t=1258665"), bullet point 2.

---

### Post by scu-ba-de-buntu on 2010-06-14
I was using KDevelop 3.5.3 (which uses KDE 3.5.10). I do not believe that should really matter, since the following typed in terminal works fine:

g++ -o"%e" ./%e.o -L/usr/lib -lalleg-4.2.2 -lm -lXxf86vm -lXcursor -lXpm -lXext -lX11 -lpthread -ldl

Therefore I have concluded that KDevelop is not ready for prime use yet, and have decided to use Code::Blocks.

Still, I would be curious to know if there is a way to do this, either in this release or a future release.

Thanks

---

### Post by Zugzwang on 2010-06-14
> **scu-ba-de-buntu said:**
> I was using KDevelop 3.5.3 (which uses KDE 3.5.10). I do not believe that should really matter, since the following typed in terminal works fine:


Well, the "building framework" matters. Which one is it? Qmake? Custom makefiles? CMake? Autotools? When you created your project in the first place, you have to choose one, and it is important to know which it was.

---

### Post by scu-ba-de-buntu on 2010-06-14
Hmm.. I guess I don't know enough about "building framework"s. I just have my main.c, main.h, and my libs I wrote.

That was really quick, btw. Zugzwang, thanks for your help so far!

---

### Post by James78 on 2010-06-14
Usually you link the libraries using CMake or whatever build framework you chose to use. I use KDevelop 4, so I had to write some CMake modules to find the library paths, include files, etc, then generate variables to be put inside the build environment, worked like a charm, and it was done the correct way. The "cheap" way would be to simple append those arguments onto the end of the programs executed commands, in CMake it was exe_linker_flags or something similar.

So basically, you should find out what build framework you're using, then search how to do it using it.

---

