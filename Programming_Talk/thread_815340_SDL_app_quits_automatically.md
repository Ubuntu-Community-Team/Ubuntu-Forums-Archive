---
title: "SDL app quits automatically"
date: 2008-06-01
forum: Programming Talk
---

### Post by arseniy on 2008-06-01
When I run the app (using SDL), the windows pops up, successfully, and then quits instantly. I see it pop up and go away. Then, Code::Blocks says "Process terminated with status 1 (0 minutes, 0 seconds)". Why does this keep happening? I'm just following the tutorial at [http://www.sdltutorials.com/sdl-coordinates-and-blitting/]("http://www.sdltutorials.com/sdl-coordinates-and-blitting/"), and when I get to halfway down that part of the tutorial, the bitmap drawing part, that's when it happens. Any ideas? I have exactly the same files the tutorial has, so if you need the code check there. Thanks :)

---

### Post by Can+~ on 2008-06-01
Sounds like a segmentation fault, debug it, find where you are trying to access a NULL pointer, an array out of range, etc.

---

### Post by Zugzwang on 2008-06-02
Unlike Can+~, I do not think that the error is caused by some illegal access/whatever (which doesn't necessarily mean that he/she is wrong. ;-) ). Use a debugger and execute the program step-by-step. Then identify the line of code in which the program doesn't behave as wanted. It's not unlikely here that some step of the initialisation phase fails. Alternatively, you can change the program to output some debugging information after each step.

---

