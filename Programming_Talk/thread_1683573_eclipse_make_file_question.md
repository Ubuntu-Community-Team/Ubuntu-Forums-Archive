---
title: "eclipse make file question"
date: 2011-02-07
forum: Programming Talk
---

### Post by pythonsyntax on 2011-02-07
How do i make my own make file in eclipse C/C++?

---

### Post by pythonsyntax on 2011-02-07
Anyone?

---

### Post by Simian Man on 2011-02-07
If you choose "Makefile Project" in the new project menu Eclipse will use your existing Makefile instead of its own builder.

---

### Post by pythonsyntax on 2011-02-08
What you mean i have to build my own make files?

---

### Post by Simian Man on 2011-02-08
With Eclipse, you can either use their built-in source code builder, or you can use your own makefile.  If you don't know what a makefile is, or how to build one, then using Eclipse's built-in builder would make more sense.

---

### Post by GregBrannon on 2011-02-08
> **pythonsyntax said:**
> How do i make my own make file in eclipse C/C++?

Then:

> What you mean i have to build my own make files?

Doesn't make sense. Maybe you didn't ask the right question.

---

### Post by pythonsyntax on 2011-02-12
Can i use C/C++ in raw sockets in eclipse?

---

### Post by Some Penguin on 2011-02-12
> **pythonsyntax said:**
> Can i use C/C++ in raw sockets in eclipse?

Why would it stop you?  The answer will only be 'no' if you don't bother to learn how.

---

### Post by pythonsyntax on 2011-02-14
The reason i was asking it becuase i thought you had to be in main root for it.And you don't need to be rude about it!

---

### Post by Zugzwang on 2011-02-14
> **pythonsyntax said:**
> The reason i was asking it becuase i thought you had to be in main root for it.And you don't need to be rude about it!

Ah, OK. For clarity, it would have been better if you had added that this is your concern to your original post.

The point is that we could not have guessed that this "being root"-issue was your concern when asking the question as it doesn't exist (and is in fact unrelated to eclipse - you can easily develop your code in eclipse and then run your compiled program as the root user if you wish). Of course you can open a socket while not being root. Only the ones with numbers < 1024 are reserved for the root (I don't know about socket 1024 itself, though).

---

