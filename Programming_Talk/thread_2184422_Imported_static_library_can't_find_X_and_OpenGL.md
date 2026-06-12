---
title: "Imported static library can't find X and OpenGL"
date: 2013-10-29
forum: Programming Talk
---

### Post by JoshKlint on 2013-10-29
I am using C++ with Code::Blocks and GCC.

I have a static library (.a) file I compiled myself in another project.  The static library uses X and OpenGL.

When I import the static library into a project, and set the project up to link to X and OpenGL, I get a lot of "undefined reference to..." error for every single X or OpenGL command the static library calls.  If I compile the static library as a dynamic library (.so) it works fine.  If I run the static library project as its own executable, it works fine.

-------------------------

During the course of describing this question, I found the answer.  Code::Blocks has a little control to the right of the linker library list that lets you control the order.  I had to place my dependent static lib at the top, above the place where OpenGL and X11 are added.  Unintuitive, but it solved the problem.

I am posting this anyways for the benefit of other people who encounter this problem.

---

