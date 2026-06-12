---
title: "gcc for .cpp? v. no sudoer permission"
date: 2008-10-16
forum: Programming Talk
---

### Post by ranthal on 2008-10-16
Hey all,

I am running into the standard .cpp compilation error in gcc:

error trying to exec 'cc1plus': execvp: No such file or directory

I have successfully compiled the code at home using g++ so I know that will work, however I am running this on a lab machine at school that does not have g++ and I do not have sudoer permissions which makes this problem slightly more unique than many of the other cases of it I have found.

Any suggestions?

---

### Post by snova on 2008-10-16
cc1plus is the backend to G++ that does the actual work. gcc and g++ (as well as all the other commands) are just wrappers that work out what to do (and what not to do) and in what order. (preprocessor -> compiler -> assembler -> linker)

I think you're stuck. gcc knows that cc1 is used to compile C and that cc1plus is used to compiler C++, but if it isn't there, what can it do?

There's no solution for a missing program except to install it, of course, but if you don't have admin rights, all I can say is to find somebody who does. :(

Alternatively, if you have a lot of time, you can always download the sources and build G++ yourself. It takes a while, though, because it actually compiles itself three times to make sure it gets built correctly. Fortunately you shouldn't have to build anything but the compiler- binutils are already installed.

If you go that route, you need the base package and the C++ package. Unpack them into the same directory (so they overlap) and ./configure should automatically detect the C++ compiler.

---

### Post by ranthal on 2008-10-16
> **snova said:**
> cc1plus is the backend to G++ that does the actual work. gcc and g++ (as well as all the other commands) are just wrappers that work out what to do (and what not to do) and in what order. (preprocessor -> compiler -> assembler -> linker)

Ah I see, makes sense why gcc and g++ had the same man pages.

> **snova said:**
> I think you're stuck. gcc knows that cc1 is used to compile C and that cc1plus is used to compiler C++, but if it isn't there, what can it do?

Is that typical then that it won't come w/ cc1plus?  I did run into this on other machines where I was a sudoer but why would GNU bother having it recognize .cpp if the default machine is not set up to compile it?

> **snova said:**
> There's no solution for a missing program except to install it, of course, but if you don't have admin rights, all I can say is to find somebody who does. :(

Alternatively, if you have a lot of time, you can always download the sources and build G++ yourself. It takes a while, though, because it actually compiles itself three times to make sure it gets built correctly. Fortunately you shouldn't have to build anything but the compiler- binutils are already installed.

If you go that route, you need the base package and the C++ package. Unpack them into the same directory (so they overlap) and ./configure should automatically detect the C++ compiler.

Not much time, I was planning on demoing this for the research class I am supervising at 2:30 pm.  Professor has sudoer permissions (and I should honestly just ask him to add me) but doubt he can get it set up in time.  How long does the G++ build take?  Sounds like more time than I have.

Bad news for me, but A+ response

---

### Post by LaRoza on 2008-10-16
Did you install "build-essential"?

---

### Post by geirha on 2008-10-16
What OS is on the lab computer? It may have a different c++ compiler. [http://en.wikipedia.org/wiki/List_of_C%2B%2B_compilers_and_integrated_development_environments#C.2FC.2B.2B_compilers](http://en.wikipedia.org/wiki/List_of_C%2B%2B_compilers_and_integrated_development_environments#C.2FC.2B.2B_compilers)

---

### Post by Rich78 on 2008-10-16
You need g++, or if the lab machine has g++, it's version is different to that of gcc.

If you're able to compile at home and bring it in to run, then that's one solution.  If it's to be coded and compiled on the lab machine, assuming you have permission to do this by the provider of the lab machine, then you should be able to request them to provide you with a c++ compile such as g++ and install it for you.

---

### Post by snova on 2008-10-16
The OS doesn't matter very much. This is GCC for certain.

GCC has many different language frontends, including Java, Ada, Fortran, Objective C, D, and plenty more I've never heard of.

The common frontend 'gcc' just looks at the file extension and picks one to run on it.

The gcc package includes the C compiler, and the g++ compiler contains the C++ compiler. (The build-essential package conviently depends on both.)

I think it's probably for the better that the various wrappers can recognize most of the supported languages, since then it's more flexible with which one you call, although they have different effects sometimes, such as linking in C++ support libraries automatically (you can do it manually to cut down on binary size, of course).

Besides, how is it supposed to know what backends are installed and which aren't?

Building it will take a good long time. It's easier to just ask the professor to install G++.

I hope I'm not too late...

---

