---
title: "Taking a systems programming in unix class, what do I need to know/refresh myself on"
date: 2012-01-19
forum: Programming Talk
---

### Post by venom104 on 2012-01-19
Hello everyone, happy internet blackout day. Anyway, as the title says, I'm enrolled in a systems programming in unix course. Here is what the course description is...

"[FONT=Arial][SIZE=2]This course covers the features of the C  language commonly used in systems programming, and the application of  those features to systems programming in a Linux/UNIX environment.  Topics include C preprocessor macros, input/output, bit-manipulation  facilities; timesharing system concepts; shell script programming; make  files and source code control; basic system calls including fork and  exec; pointers and dynamic memory allocation; libraries; and relocation  and linking concepts including assembler handling of symbol tables."

Anyway, my question is, what do I really need to know for this course (yes, I already know I need to know C)? I'm assuming I need a refresher on pointers and the STL functions, but what else? What data structures should I review, what algorithms, what programming concepts do I need to be an expert at.

Getting an A in this class is important to me since I'm taking it purely out of interest [/SIZE][/FONT][FONT=Arial][SIZE=2](it's not required by for my degree) [/SIZE][/FONT][FONT=Arial][SIZE=2]so I could use all the help possible. 

EDIT:

I forgot to say we're using a debian sid live cd in class
[/SIZE][/FONT]

---

### Post by Bachstelze on 2012-01-19
AFAIK STL is a C++ thing, not C. I'd say just know C, but know it very well. In system programming perhaps more than in other areas, you need to know EXACTLY how your program behaves, because consequences of unexpected behavior can be more dramatic. By experience, academics are sometimes quite sloppy in their use of C, so in terms of actual programming, don't take anything you see at face value. (No, it is not okay to directly store the return value of getchar() into a char. No, it is not okay to have void main(). No, it is not okay to just cast unsigned to signed. Etc.)

---

### Post by trent.josephsen on 2012-01-19
You need to know the difference between C and C++.  Not for the course, just so that I don't track you down and rip your heart out while you sleep.

Be very familiar with standards-compliant C.  Find a forum dedicated specifically to C and hang out there until you know how to avoid the rookie mistakes.  (I started with comp.lang.c, which isn't bad if you can avoid the spam, but don't post unless you're thick-skinned.)

---

