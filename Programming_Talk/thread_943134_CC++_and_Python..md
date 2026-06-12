---
title: "C/C++ and Python."
date: 2008-10-09
forum: Programming Talk
---

### Post by rnodal on 2008-10-09
Hello all:

One of the goal of my game engine is to allow the developer to write certain part of the game via a script because of of the obvious benefits of interpreted code over compiled code. I chose python to be the scripting language that I would like to support (at least the first one :)). So my question is what ways (or way) do you recommend for this. I know that you can extend Python by writing a C module but in that case the main program still the Python interpreter. I do not want it that way. I want the C/C++ program to be the main one. I have started to read from the the Python documentation and it seems that the way to go is to embed the Python interpreter into the C/C++ application. Since I have not read much I was wondering if you could help get a head start from what you have experienced. A quick note, I would like to release my engine under LGPL so how does embeding the interpreter into my application will affect that? Thanks all for your time.

-r

---

### Post by rnodal on 2008-10-09
Is this the correct way? Or recommended way?
[http://www.python.org/doc/2.5.2/ext/extending-with-embedding.html](http://www.python.org/doc/2.5.2/ext/extending-with-embedding.html)

-r

---

### Post by kknd on 2008-10-09
Steps:

1 - Create an interpreter instance inside your program;
2 - Expose the functions that you want to the scripts have access, registering them in the interpreter instance;
3 - Load the user scripts and tell the interpreter to execute them;

Edit: Yes, thats the correct way.

---

### Post by rnodal on 2008-10-09
Thanks for the quick reply. One more question is it possible to link statically the Python interpreter? Technically and legally? I read the license and it seems to me that legally it is possible.

[http://www.python.org/psf/license/]("http://www.python.org/psf/license/")

Thanks!

-r

---

### Post by kknd on 2008-10-11
Yes, the license is very liberal!

P.S: Have you tried Lua? Its smaller, simpler and faster, very suitable for a game. It's C API its very easy too.

---

### Post by rnodal on 2008-10-11
First, thanks a lot for your time. Second, thanks for your suggestion. My plan is to support python/lua and any other scripting language that has the same convenience in terms of easy to embed. One more time, thanks!

-r

---

