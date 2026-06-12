---
title: "Contributing to existing projects, in QtCreator"
date: 2011-07-02
forum: Programming Talk
---

### Post by Spitted on 2011-07-02
Hi

I'm kinda new to Linux programming and I want to contribute to Open Source.
I cloned the PCManFM project from Git (it's the file manager in lubuntu) and played with it a little using regular text editors but it was really uncomfortable.
So yesterday I discovered QtCreator which actually blew my mind. I tried many IDEs in Linux but they all sucked some way or another. But the problem is, since PCManFM supplies only autogen.sh script for configuring and building, and no QtCreator proj file or CMakeLists, QtCreator cannot open it as a project and I lose all it's awesome advantages.
What is the common solution for this? If most projects don't provide something like CMakeLists why even bother creating so many IDEs?
I really hope the answer won't be to create a new QtCreator project and configure it manually while transcribing the Makefile...

Thanks,
Eyal

---

### Post by Spitted on 2011-07-02
Is it okay to bump the thread?

---

### Post by Vox754 on 2011-07-02
> **Spitted said:**
> Hi

I'm kinda new to Linux programming and I want to contribute to Open Source.
I cloned the PCManFM project from Git (it's the file manager in lubuntu) and played with it a little using regular text editors but it was really uncomfortable.
So yesterday I discovered QtCreator which actually blew my mind. I tried many IDEs in Linux but they all sucked some way or another. But the problem is, since PCManFM supplies only autogen.sh script for configuring and building, and no QtCreator proj file or CMakeLists, QtCreator cannot open it as a project and I lose all it's awesome advantages.
What is the common solution for this? If most projects don't provide something like CMakeLists why even bother creating so many IDEs?
I really hope the answer won't be to create a new QtCreator project and configure it manually while transcribing the Makefile...

Thanks,
Eyal

I think creating the QtCreator project would be the solution, or persuading the original developers to do it themselves.

It is as in everything, people disagree on what is best.

For some people IDEs are good, and help them be more productive. Others dislike the complexity and additional bloat.

You may think that nowadays developers should use all the awesome features of modern IDEs, but I am sure there are still people who prefer to code the old way, on a terminal, and compiling likewise.

---

### Post by hakermania on 2011-07-02
Well, you could manually make the project file yourself as far as I know.
You can run
```
qmake -project
```
in the source code, link to any necessary libs to the .pro file and then
```

qmake *.pro
qmake
make

```
and that ould do the trick ;)

I don't know if it is so simple :/
But for my C/C++ simple programs when all of my Source Code is in a single folder, it is!

---

### Post by Spitted on 2011-07-03
It's not a problem when all I do is compile a couple of source files. But when some dependencies, library links and special compile flags must be performed, creating the project can be hard.

---

### Post by mourt on 2011-12-20
Qt Creator recently gained direct support for autoconf/automake based projects. Maybe that helps you.

---

