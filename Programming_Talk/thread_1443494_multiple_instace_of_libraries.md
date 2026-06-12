---
title: "multiple instace of libraries"
date: 2010-03-31
forum: Programming Talk
---

### Post by Mr.Carramba on 2010-03-31
Hi,

I want C++ to use C file and functions with in. Further I want several instances of this C application. Therefore, I create a C++ class which suppose to use C app.
I have tried not to create a static library and compile C++ app, and I have tried with shared library approach.

Problem that I'm having is that variables that are in C library changes from each C++ class instance.

I have this simple test case [http://pastebin.com/56N8AhGU](http://pastebin.com/56N8AhGU) with static library.
Variable event, will be changed by obj t1 and when t1.

What I would like to to have two instances of this c library in memory. So that each c++ class have "this own library".

The assumption is that there is nothing I can do about C library, and variables are not protected in any way.

---

