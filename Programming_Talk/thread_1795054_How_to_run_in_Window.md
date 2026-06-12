---
title: "How to run in Window"
date: 2011-07-02
forum: Programming Talk
---

### Post by kelvin490 on 2011-07-02
I have a simple C program compiled in ubuntu and an excution file is produced. I wonder how can I put it in window and run it. Anyway can I run this program in Window?
 
Thank you.

---

### Post by zobayer1 on 2011-07-02
> **kelvin490 said:**
> I have a simple C program compiled in ubuntu and an excution file is produced. I wonder how can I put it in window and run it. Anyway can I run this program in Window?
 
Thank you.

using terminal, change directory to where your executable is, say it is named a.out, then just hit:
```

./a.out

```

---

### Post by kelvin490 on 2011-07-02
> **zobayer1 said:**
> using terminal, change directory to where your executable is, say it is named a.out, then just hit:
```

./a.out

```
 
 
But can I run it in Window XP? I tried double click but it doesn't work

---

### Post by zobayer1 on 2011-07-02
> **kelvin490 said:**
> But can I run it in Window XP? I tried double click but it doesn't work

Ow, you have written "Window" which should be "windows".
This is pretty obvious that you CAN'T do such things. If you need to run in windows, you need to compile in windows environment. C/C++ executable is not platform independent.

---

### Post by zobayer1 on 2011-07-02
And if you need a ide in windows, you can quickly download and install Dev C++ which is a small software and really easy to use.

---

### Post by kelvin490 on 2011-07-02
> **zobayer1 said:**
> And if you need a ide in windows, you can quickly download and install Dev C++ which is a small software and really easy to use.
 
Thank you. I see the problem now. Any compiler that is suitable to compile a C program in Windows OS ?

---

### Post by Dhiraj Thakur(Invincible) on 2011-07-02
> **kelvin490 said:**
> Thank you. I see the problem now. Any compiler that is suitable to compile a C program in Windows OS ?
Borland turbo c++,dev c++ as zobayer1 mentioned are out thre u can do a simple google search....

---

### Post by cgroza on 2011-07-02
> **zobayer1 said:**
> And if you need a ide in windows, you can quickly download and install Dev C++ which is a small software and really easy to use.
I thought that thing is no longer updated.
Code::Blocks is a good IDE too for C languages although I am sure the OP does not need all that power in which case a semi-IDE text editor like Geany will do the trick.

---

### Post by zobayer1 on 2011-07-02
> **cgroza said:**
> I thought that thing is no longer updated.
Code::Blocks is a good IDE too for C languages although I am sure the OP does not need all that power in which case a semi-IDE text editor like Geany will do the trick.

I intentionally left codeblocks behind, because I have heard that it's installation is not simple as dev c++. I used codeblocks in ubuntu, but never in windows before. But I thikn Dev C++ is still quite ok, just for quick compiling. For windows, I would always go for Visual Studio 9. But new programmers may find that software difficult to use.

---

### Post by andrew1992 on 2011-07-03
Code::Blocks in Windows works out of the box if you get the version bundled with MinGW.

---

### Post by unknownPoster on 2011-07-03
It is possible to create windows executables in Linux using a process known as cross-compiling, but that's a relatively advanced subject.

---

### Post by cgroza on 2011-07-03
> **unknownPoster said:**
> It  is possible to create windows executables in Linux using a process  known as cross-compiling, but that's a relatively advanced  subject.
I doubt the OP needs to do that. If he is learning, using the standard platform 
compiler should be fine.

---

### Post by unknownPoster on 2011-07-03
> **cgroza said:**
> I doubt the OP needs to do that. If he is learning, using the standard platform 
compiler should be fine.

Regardless of what the OP "needs" it is what he wants. Not telling him about the possibility would be a disservice.

---

### Post by JupiterV2 on 2011-07-03
msys/mingw may also serve your needs. msys is a minimal POSIX compatible system for building software on windows. Alternatively, you could use Cygwin but I personally rejected it because any software compiled on it has a dependency on cywin.dll (or something like that) which was not acceptable to me.

---

