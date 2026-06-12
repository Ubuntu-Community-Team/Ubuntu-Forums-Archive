---
title: "Programming in C/++"
date: 2011-07-13
forum: Programming Talk
---

### Post by createdcreature on 2011-07-13
What should I use to program in C in Linux? I have absolutely no idea where to start! I am an expert in C, but not in what to compile it in Linux?

---

### Post by cgroza on 2011-07-13
GCC and <insert IDE or editor here>. I recommend emacs...:)

---

### Post by TwoEars on 2011-07-13
How can you manage to be an expert in C, and yet not be able to find a compiler for it?

[http://en.wikipedia.org/wiki/List_of_compilers#C_compilers](http://en.wikipedia.org/wiki/List_of_compilers#C_compilers)

The standard is gcc, but clang is up and coming.

Here is a list of IDEs, if you need them too - 

[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B)

Google, isn't it wonderful?

---

### Post by haqking on 2011-07-13
> **Robert Moyse said:**
> What should I use to program in C in Linux? I have absolutely no idea where to start! I am an expert in C, but not in what to compile it in Linux?


an expert biut dont know how to compile it ?

gcc and vim

And a good book by the sounds of it ;-)

---

### Post by psusi on 2011-07-13
+1 for emacs.  It isn't as pretty or easy to figure out as visual studio, but it's a hell of a lot more powerful.

---

### Post by Npl on 2011-07-13
Hes is more than an expert, he is a script himself (look at his location). None of his posts take anything said in the thread in context, even if it sometimes fits the topic.

---

### Post by cgroza on 2011-07-13
> **Npl said:**
> Hes is more than an expert, he is a script himself (look at his location). None of his posts take anything said in the thread in context, even if it sometimes fits the topic.
I have this doubt ever since I saw his first post.

---

### Post by Npl on 2011-07-13
> **cgroza said:**
> I have this doubt ever since I saw his first post.More than just a doubt, if not he can prove me wrong, quote my post and say something thats more fitting than random fortune cookies for IT personal

---

### Post by createdcreature on 2011-07-14
How do I compile a C++ command line program in Linux? I am an expert in C++, but not in compiling in Linux! This follows up to my 'Programming in C' thread.

---

### Post by stchman on 2011-07-14
> **Robert Moyse said:**
> How do I compile a C++ command line program in Linux? I am an expert in C++, but not in compiling in Linux! This follows up to my 'Programming in C' thread.

Most of the time you will use the g++ command line compiler.  What OS and what IDE did you use for your C++ development?

Alsp for Ubuntu, make sure you install build-essential.

```

sudo apt-get install build-essential

```

---

### Post by Elfy on 2011-07-14
Merged.

---

### Post by createdcreature on 2011-07-14
Ok. I will use GCC and G++.

---

### Post by createdcreature on 2011-07-25
Working really well!

me@mypc: g++ program.cpp

me@mypc: ./a.out

   Hello world!

---

### Post by createdcreature on 2011-07-28
Just one question, can I distribute the binaries with Linux computers without gcc/g++ installed and Mac OS X users (because Mac OS X is basically FreeBSD)?

---

### Post by nvteighen on 2011-07-28
> **Robert Moyse said:**
> Just one question, can I distribute the binaries with Linux computers without gcc/g++ installed and Mac OS X users (because Mac OS X is basically FreeBSD)?

The compiler isn't needed to run the executables, so there's no requirement to have gcc/g++ installed for that. But you ought to have the runtime libraries installed.

But: executable formats are different across OSs. Yes, Darwin (the system underlying Mac OS X) is based on FreeBSD, but uses a different kernel (XNU) and uses the Mach executable format. IIRC, FreeBSD mostly uses ELF.

Recompiling is the best bet.

---

### Post by psusi on 2011-07-29
> **nvteighen said:**
> Yes, Darwin (the system underlying Mac OS X) is based on FreeBSD, but uses a different kernel (XNU) and uses the Mach executable format. IIRC, FreeBSD mostly uses ELF.


I never understand why people say this kind of thing.  FreeBSD is a kernel, so saying that MacOS is based on FreeBSD,  but using a different kernel, is complete nonsense.  They have a microkernel based on Mach, on top of which they have implemented POSIX APIs.  That doesn't have anything to do with FreeBSD, other than FreeBSD also implements POSIX APIs... as does Linux, and even Windows implements many of them.

---

### Post by nvteighen on 2011-07-29
> **psusi said:**
> I never understand why people say this kind of thing.  FreeBSD is a kernel, so saying that MacOS is based on FreeBSD,  but using a different kernel, is complete nonsense.  They have a microkernel based on Mach, on top of which they have implemented POSIX APIs.  That doesn't have anything to do with FreeBSD, other than FreeBSD also implements POSIX APIs... as does Linux, and even Windows implements many of them.

FreeBSD isn't a kernel, but the name of an BSD-derived OS as a whole. It's a kernel and a userland... and is a completely different OS to e.g. Debian GNU/kFreeBSD (I guess the lowercase 'k' stays for "kernel"), which combines FreeBSD's kernel (which AFAIK, doesn't have a special name) with the GNU userland and Debian's official software.

Apple Darwin has its userland derived from FreeBSD's and its XNU kernel has some parts derived from FreeBSD's kernel, but also from the Mach kernel and others.

---

### Post by stchman on 2011-07-29
> **psusi said:**
> I never understand why people say this kind of thing.  FreeBSD is a kernel, so saying that MacOS is based on FreeBSD,  but using a different kernel, is complete nonsense.  They have a microkernel based on Mach, on top of which they have implemented POSIX APIs.  That doesn't have anything to do with FreeBSD, other than FreeBSD also implements POSIX APIs... as does Linux, and even Windows implements many of them.

The Mach kernel contains parts from FreeBSD and NetBSD.  Those parts were incorporated into NextSTEP which is the core of OS X.  So OS X has underpinnings of FreeBSD.

---

### Post by createdcreature on 2011-07-30
Isn't a.out the Linux binary system that was replaced ages ago by ELF, so all systems should have the runtime?

---

### Post by stchman on 2011-08-02
> **Robert Moyse said:**
> Isn't a.out the Linux binary system that was replaced ages ago by ELF, so all systems should have the runtime?

In gcc and g++ it is just the default filename if no name is specified.

---

