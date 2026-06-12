---
title: "Code::Blocks &quot;host application&quot; and LD_LIBRARY_PATH"
date: 2008-12-14
forum: Programming Talk
---

### Post by Andruk Tatum on 2008-12-14
I recently came across Code::Blocks, and I am attempting to transition to using it instead of my own custom makefile for a project of mine.  The project is a shared library, and I have a test executable to test out all of the functions in the library.

When I was just using my makefile, I would make the project and then run the project with
```
LD_LIBRARY_PATH=.. ./test
```

I have used the EnvVar plugin to setup LD_LIBRARY_PATH:
LD_LIBRARY_PATH = $(LD_LIBRARY_PATH):../<project>:./bin/Debug

As it stands now, I can compile the library perfectly in C::B, but I cannot run or debug the library.  I attempted to set the host application to ./test, but when I use C::B to "Run", I get
```
Executing: test  (in /home/<me>/<project>/.)
Process terminated with status 1 (0 minutes, 0 seconds)
```

If anybody has any insight as to how to get C::B to run my test executable and load my library for it, I would be very grateful.

Thanks in advance.

---

### Post by Jonas thomas on 2008-12-14
I've just started playing around with code::blocks and wxwidgets
Perhaps [this]("http://www.metalshaperman.com/?p=111") may give you some idea's as to what to try...

JT

---

### Post by Andruk Tatum on 2008-12-14
Thanks for that, I hadn't seen that before.

I think I have everything compiling correctly, but I can't launch the host application and instruct it to load the correct libraries *within C::B*.  So I don't think it's a compile error, but a loading error on launch.

---

### Post by Jonas thomas on 2008-12-14
> **Andruk Tatum said:**
> Thanks for that, I hadn't seen that before.

I think I have everything compiling correctly, but I can't launch the host application and instruct it to load the correct libraries *within C::B*.  So I don't think it's a compile error, but a loading error on launch.

It not like I have hundreds of IDE's under my belt, but what I've seen so far in C:B I like.  Best of all it runs in MSW as well as Linux.  Have you discovered right clicking on a class or a constant and selected find the declaration??

---

