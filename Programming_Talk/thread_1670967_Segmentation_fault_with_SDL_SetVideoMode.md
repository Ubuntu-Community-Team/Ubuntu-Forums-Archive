---
title: "Segmentation fault with SDL_SetVideoMode"
date: 2011-01-19
forum: Programming Talk
---

### Post by tommy549 on 2011-01-19
I'm currently working on an SDL project for my high school computer science class. When I run it, I get a SIGSEV error from codeblocks, and when I run the debugger, it shows that the program crashes at the line of code:
```
screen = SDL_SetVideoMode(1024, 768, 32, SDL_SWSURFACE | SDL_DOUBLEBUF | SDL_RESIZABLE);
```screen is a member of the class that SetVideoMode() is called in and my teacher doesn't know whats wrong. Can anyone help me?

---

### Post by Arndt on 2011-01-20
> **tommy549 said:**
> I'm currently working on an SDL project for my high school computer science class. When I run it, I get a SIGSEV error from codeblocks, and when I run the debugger, it shows that the program crashes at the line of code:
```
screen = SDL_SetVideoMode(1024, 768, 32, SDL_SWSURFACE | SDL_DOUBLEBUF | SDL_RESIZABLE);
```screen is a member of the class that SetVideoMode() is called in and my teacher doesn't know whats wrong. Can anyone help me?

Can you repeat the error with a very small program?

---

### Post by tommy549 on 2011-01-20
> **Arndt said:**
> Can you repeat the error with a very small program?
 
I made a small project that just drew a picture, and it didn't give me an error. I copied all of my code that had anything to do with graphics from my old project into my new one.

---

### Post by psusi on 2011-01-20
Inspect the this pointer and/or move up the call stack to the calling code.  You are probably calling the method on a null pointer.

---

### Post by tommy549 on 2011-01-20
> **psusi said:**
> Inspect the this pointer and/or move up the call stack to the calling code. You are probably calling the method on a null pointer.
 
Thank you very much. I checked and it turned out I didn't initialize something properly. I probably never would have caught that otherwise :D

---

### Post by tommy549 on 2011-01-20
> **psusi said:**
> Inspect the this pointer and/or move up the call stack to the calling code. You are probably calling the method on a null pointer.
 
Thank you very much. I checked and it turned out I didn't initialize something properly. I probably never would have caught that otherwise :D

---

