---
title: "I don't know what compilers I have"
date: 2006-05-30
forum: Programming Talk
---

### Post by walkingbeard on 2006-05-30
Hi

I'm trying to compile this bit of nothing in Anjuta, to test the compilation process.  It doesn't work - I get this: sh: g++: command not found

So I looked in synaptic to find out what's going on.  I have the following packages installed:

gcc-3.3-base      I have to have this, for xorg-driver-fglrx
gcc-4.0               I installed these myself
gcc-4.0-base
gcc-4.0-doc
cpp
cpp-4.0

What's going on?  The g++ packages are only available in 2.95 and 3.4 flavours.  This all seems a bit disorganised.

Help would be appreciated

---

### Post by Lord Illidan on 2006-05-30
[quote=walkingbeard]Hi

I'm trying to compile this bit of nothing in Anjuta, to test the compilation process.  It doesn't work - I get this: sh: g++: command not found

So I looked in synaptic to find out what's going on.  I have the following packages installed:

gcc-3.3-base      I have to have this, for xorg-driver-fglrx
gcc-4.0               I installed these myself
gcc-4.0-base
gcc-4.0-doc
cpp
cpp-4.0

What's going on?  The g++ packages are only available in 2.95 and 3.4 flavours.  This all seems a bit disorganised.

Help would be appreciated[/quote]

Gcc is the c compiler, g++ is the c++ compiler.

Have you done : ```
sudo apt-get install build-essentials
```

---

### Post by walkingbeard on 2006-05-30
There doesn't appear to *be* a build-essentials

---

### Post by walkingbeard on 2006-05-30
It's build-essential - no s! :-D

---

### Post by Lord Illidan on 2006-05-30
[quote=walkingbeard]There doesn't appear to *be* a build-essentials[/quote]
Quite right. It is build-essential . Sorry.

---

