---
title: "Programming in C# on Ubuntu"
date: 2008-07-19
forum: Programming Talk
---

### Post by themostunoriginalname on 2008-07-19
I just installed Mono 1.2.6 on Ubuntu Gutsy.

I am completely new to C#, but I have programmed in C, C++, Java, Python, PHP, etc..., so although I'm testing new waters, the concept of programming isn't new to me.

I tried googling on how mono works and how I can compile C# programs on it, but I can't find any. Do you guys have a tutorial lying around or tutorial somewhere on the web about using mono and programming in C#?

---

### Post by LaRoza on 2008-07-19
[http://ubuntuforums.org/showthread.php?t=815651&highlight=mcs](http://ubuntuforums.org/showthread.php?t=815651&highlight=mcs)

---

### Post by themostunoriginalname on 2008-07-19
Thakns

---

### Post by true_friend on 2008-07-20
Mono 1.2.9 can be downloaded [for Hardy]("http://www.mono-project.com/Other_Downloads#Ubuntu_8.04_LTS_.28Hardy_Heron.29_-_official_packages:") as well.

---

### Post by sakabato on 2008-07-23
please use gmcs instead of mcs

---

### Post by LaRoza on 2008-07-23
> **sakabato said:**
> please use gmcs instead of mcs

Something with some expertise. :-)

What is the difference?

---

### Post by Zugzwang on 2008-07-23
> **LaRoza said:**
> 
What is the difference?

The difference is that "mcs" compiles for .Net 1.1 while "gmcs" compiles for .Net 2.0. Since .Net 1.1 doesn't have generics and Mono now supports 2.0, "mcs" is quite outdated.

---

### Post by LaRoza on 2008-07-23
> **Zugzwang said:**
> The difference is that "mcs" compiles for .Net 1.1 while "gmcs" compiles for .Net 2.0. Since .Net 1.1 doesn't have generics and Mono now supports 2.0, "mcs" is quite outdated.

I see. I will be sure to keep my future advise up to date with the latest Microsoft...er, Mono, developments.

---

### Post by cszikszoy on 2008-07-23
more information about the difference between mcs, gmcs (and smcs) here:

[http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)

---

### Post by Kadrus on 2008-07-23
C# FAQ started by LaRoza
[FAQ: Compiling and Running C# Programs]("http://ubuntuforums.org/showthread.php?t=867818")

---

