---
title: "How Cross-Platform is C#?"
date: 2008-01-07
forum: Programming Talk
---

### Post by Majorix on 2008-01-07
I have recently managed to get my Monodevelop to work.

I was wondering though, after a lot of babbling with Python, how cross-platform is C#? Can a program coded under Windows using VS2008 be run under Linux with Mono or something similar? Can a program coded with GTK# 2 under Linux be run under Windows? And what about Mac? Solaris? BSD? etc?

Thanks a lot.

---

### Post by pmasiar on 2008-01-07
c# is somewhat cross-platform, but less crossplatform than Python, if this is what you ask.

As always, cross-platform development relies on not using libraries existing only on one platform, and on quirks between platform ironed out by someone else :-)

C# was designed to be non-crossplatform, just Mono tries to reimplement "most" of functionality from .NET on Linux.
Python was designed to be crossplatform from the very beginning.

IMHO, YMMV, IANAL.

---

### Post by Majorix on 2008-01-07
I can't get MD to auto complete the code anyways. That's probably what I love the most in an IDE. Best platform is the natural one, as always, if you ask me.

I am a software engineering student, so I will want to make money out of programming. So I will use C# under Windows (most popular on Windows) and Java on Linux (most popular on cross-platform). Probably I will also look at Python but Perl offers a lot more jobs.

Anyways enough with my babbling. Thanks for the information, pmasiar.

---

### Post by emperon on 2008-01-07
I am using mono professionally at work. I find it quite cross platform. Most of the stuff are directly portable. 
The unfortunate thing mono packages in ubuntu are old. so if you are serious in mono development make sure you know how to install mono and monodevelop from svn. (Installing monodevelop from svn is rather difficult since it depends on so many things, but it is worth I think)

---

