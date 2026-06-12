---
title: "new to monodevlop and i cant success to build solution in c# lang"
date: 2008-06-22
forum: Programming Talk
---

### Post by dinbrca on 2008-06-22
ok i am new to monodevlop and when i try to build a solution it says:
"
Building Solution Guess

Building Project: Guess (Debug)
Performing main compilation...

Build failed. Executable not found: /usr/bin/gmcs

"
what do i do?

---

### Post by descendency on 2008-06-22
install gmcs:

```
sudo apt-get install gmcs
```

while you are at it, you might as well install smcs as well:

```
sudo apt-get install smcs
```

gmcs is the C# compiler for .NET 2.0 stuff and smcs is the compiler for .NET 3.0 stuff (although it is incomplete at the moment. . .you need it to build Moonlight/Silverlight projects)

---

### Post by dinbrca on 2008-06-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smcs

---

### Post by descendency on 2008-06-22
Hmm. I think it's in another repository. I don't have ubuntu installed at the moment (my backup HDD went down :()

the gmcs should have fixed your problem though.

---

### Post by true_friend on 2008-06-22
The correct package is 
> sudo apt-get install mono-gmcs

mono-gmcs (Run this command in terminal, install it and it should work).
Regards

---

