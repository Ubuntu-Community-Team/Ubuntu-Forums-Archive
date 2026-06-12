---
title: "coding a C/C++ app to be as hard as posable to port to windows?"
date: 2008-07-11
forum: Programming Talk
---

### Post by hessiess on 2008-07-11
How can I make an application as hard as posable to port to windows? but still be open source.

---

### Post by bobbocanfly on 2008-07-11
Not sure why you would want to do this (except for a challenge) but writing things with as many Linux specific system calls etc would be a good start.

---

### Post by Phenax on 2008-07-11
Make your own license that prohibits compilation for Windows. Of course, people may still void it.

---

### Post by Zugzwang on 2008-07-11
Note that this somewhat defeats the purpose of *free* software. 

For Windows, there's also Cygwin. In order to achieve your questionable goal, you will need to use function calls that are not implemented on the Cygwin platform yet.

---

### Post by wrtpeeps on 2008-07-11
> **hessiess said:**
> How can I make an application as hard as posable to port to windows? but still be open source.

Why? Seriously. Why?!

---

### Post by nvteighen on 2008-07-11
If it's open source, there are two things that can happen:

1. That people rewrite your code to run under Windows.
2. That people read your code, say it's useless and reimplement a cross-platform open-source application you won't be able to compete against.

Any reason to do such a thing?

---

### Post by hessiess on 2008-07-11
my reasoning is based around the fact that it is posable to wright a windows application that is hard to port, by using DirectX for example. I was wondering if it would be posable to do the same thing on Linux.

---

### Post by bruce89 on 2008-07-11
> **hessiess said:**
> my reasoning is based around the fact that it is posable to wright a windows application that is hard to port, by using DirectX for example. I was wondering if it would be posable to do the same thing on Linux.

As Linuxy things are usually free/open, no.

---

### Post by nvteighen on 2008-07-11
> **hessiess said:**
> my reasoning is based around the fact that it is posable to wright a windows application that is hard to port, by using DirectX for example. I was wondering if it would be posable to do the same thing on Linux.
Yes, MS does that all the time, but they use proprietary licenses that make them use advantage from non-portability. An open source/free software program wouldn't be able to survive using that approach.

To keep it absolutely non-portable, you have to lock your program's code from the public. Otherwise, people will always find a way to make it portable.

---

### Post by LaRoza on 2008-07-11
> **hessiess said:**
> How can I make an application as hard as posable to port to windows? but still be open source.

I see you are using a language that doesn't exist "C/C++", so it will be hard to port anywhere ;)

The reason why Windows apps are hard to port is they are either closed source (MS Office), or use proprietary libraries (ActiveX). Linux doesn't really have things like that in the open source world; nothing is closed source and libraries are also free.

---

### Post by thk on 2008-07-11
#ifdef .NET
*NULL;
#endif

---

### Post by gnusci on 2008-07-11
Why?... That is not the correct way... You don't need to behave as they do... don't learn those things from MS, they just think about themselves... be free... be GNU.

---

### Post by pmasiar on 2008-07-12
> **hessiess said:**
> How can I make an application as hard as posable to port to windows? but still be open source.

Why? 

If your application is useful, why not also Windows users to let it use for free? Would you prefer that someone will reimplement your idea for Windows and charge for it? How that helps advancement of Free software? Would Windows users like  Linux programmers more?

And if your app is not useful, who would bother to port it?

---

### Post by kavon89 on 2008-07-12
After you finish writing the application, use an IDE like NetBeans to refactor your variable names so they're impossible to understand, single letters the works. Then mess up the indenting and remove the commenting. Release those files as the source and keep the properly written source files somewhere else.

No one will want to port it the moment they look at the code, even though it compiles.


Why don't you just keep it closed source? Going through all that trouble or going through the trouble of integrating it so heavily with a Linux operating system, as others described, that they'd have to rewrite it sort of defeats the purpose of being open source.

---

### Post by lisati on 2008-07-12
> **thk said:**
> #ifdef .NET
*NULL;
#endif
or liberally sprinkle something like the following in your code (maybe in a header file pulled in by several of the files)
```

#ifdef windows
#error Why do you want to use a virus to run your programs?
#endif

```

---

