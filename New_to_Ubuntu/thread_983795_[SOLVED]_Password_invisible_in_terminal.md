---
title: "[SOLVED] Password invisible in terminal?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-16
I dont know what I have done to cause this.

If I type sudo su it asks for my password but when i enter my username password its invisible like nothing is happening when i hit enter after typing it though I'm logged as root so it does work.

Is this a new security feature or somthing?

---

### Post by reyhan on 2008-11-16
yes.. thats the security feature

---

### Post by corkscrew on 2008-11-16
So this must be new then? it was'nt doing that a couple of days ago?

---

### Post by reyhan on 2008-11-16
this is not the new security feature.. , all Linux always like this....

---

### Post by 3rdalbum on 2008-11-16
Sudo has always done this. Gksudo (the graphical password prompt) displays bullets; maybe you're getting confused with this?

---

### Post by bumanie on 2008-11-16
Inputting password in terminal **does not** produce a visual output - never has as far as I know.

---

### Post by Dill on 2008-11-16
From Kernighan and Pike's *The UNIX Programming Environment*:

*The UNIX system is **full duplex**: the characters you type on the keyboard are sent to the system, which sends them back to the terminal to be printed on the screen. Normally, this **echo** process copies the characters directly to the screen, so you can see what you are typing, but sometimes, such as when you are typing a secret password, the echo is turned off so the characters do not appear on the screen*.

So as far as I know, it's been around since 1969.

Cheers, 
Dylan

---

