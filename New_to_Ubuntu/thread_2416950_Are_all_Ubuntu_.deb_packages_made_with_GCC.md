---
title: "Are all Ubuntu .deb packages made with GCC?"
date: 2019-04-18
forum: New to Ubuntu
---

### Post by robertzaku1 on 2019-04-18
Hello! I just installed Ubuntu 18.10 on my HP Laptop and it works pretty good. 
I will start developing and compiling applications on Ubuntu. 
I don't know which compiler to use. Which is the most important and general one? 
I am asking because Ubuntu provides more than 70k packages online which is a huge number. So I need only a few of them, those who are more important, compilers.
Are all Ubuntu .deb packages made with pure GCC?

---

### Post by Impavidus on 2019-04-18
Gcc is probably the most popular compiler on Linux for the languages it supports. Many (most?) Ubuntu packages don't contain any compiled code and some may have been made using other compilers. But I don't see the relevance of the compiler used for creating the packages in the repositories for your own compiler choice.

---

### Post by robertzaku1 on 2019-04-19
I meant if Ubuntu has a full GCC compiler. Because there are so many packages regarding GCC. I searched for this and each package requires two or more other packages and is required by other packages. This hierarchy of packages makes me confused. I don't know what to use and how many of them. What is G++? Is it a component of GCC or has got features that GCC hasn't got? Besides that, i am aware of a GCC competitive called Clang compiler

---

### Post by Impavidus on 2019-04-20
There are several versions of gcc in the repositories, which may consist of several, sometimes optional, components. Unless you need a specific version, just install the package **gcc**. It will pull in all the dependencies it needs. **g++** is the C++ compiler, which is an optional part of gcc. You need it if you want to compile C++. You also need the development version of the libraries you want to use, as that's where you find your header files. For example, you'll need packages like **libc6-dev**, **libpng-dev**, ... Basically, every library you want to use, with the suffix -dev.

As a shortcut, some people install the package **build-essential**. It pulls in the most important packages needed for compiling: **gcc**, **g++**, **make**, **libc6-dev**. It wasn't meant to be used that way and installs some stuff you don't need, but it works.

---

