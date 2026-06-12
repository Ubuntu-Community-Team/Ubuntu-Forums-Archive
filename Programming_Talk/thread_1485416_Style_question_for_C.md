---
title: "Style question for C"
date: 2010-05-16
forum: Programming Talk
---

### Post by JDShu on 2010-05-16
I have a C program that uses header files that declare structs, and right now I have warnings that I am implicitly declaring functions. After playing around, I noticed that I either have to put the function prototype into the file that calls the functions, or into the header file to get it to compile with no warning.

My question is where should I put the prototype? I'm not sure if header files usually have both structure declarations and function prototypes, but putting the prototype into a file that doesn't define the function seems out of place. Just want to know the common practice. Thanks in advance!

---

### Post by DangerOnTheRanger on 2010-05-16
Sticking it in the header file. That's what everyone does, and it's good practice, too.

---

### Post by JDShu on 2010-05-16
Awesome, that is what I needed to know, thanks :D

---

### Post by DangerOnTheRanger on 2010-05-16
Glad to help! :)

---

### Post by Tony Flury on 2010-05-17
One word of advice - put it in a header file that make sense. The normal structure is to have a module (.c) that defines a set of common functions (maybe that operate on a common data structure), and a header file for that module that declares the public structures, and the function propototypes for that module.

---

### Post by MadCow108 on 2010-05-17
as C unfortunately does not have private and public keywords as C++, headers and prototypes are the only mean of archiving something similar.

put prototypes you want to expose to other modules in headers, and prototypes local only to the module inside the module itself (combined with static, so the symbol does not get exported globally)
like that the local functions cannot be included in other modules where they are not supposed to be used (without modifying the source at least).

---

