---
title: "C - network applications"
date: 2009-12-18
forum: Programming Talk
---

### Post by ApEkV2 on 2009-12-18
Hey there, what are some good books on programming network applications for linux? in C
example: packet redirection, packet inspection, etc

---

### Post by Xyro on 2009-12-18
Not sure about books, but this is a good site for an into to programming with sockets.

[http://beej.us/guide/bgnet/]("http://beej.us/guide/bgnet/")

If you are looking for libraries that have pre-developed tools for doing such specific things (packet inspection and such), then I've got nothing.

---

### Post by WitchCraft on 2009-12-18
> **ApEkV2 said:**
> Hey there, what are some good books on programming network applications for linux? in C
example: packet redirection, packet inspection, etc

[http://en.wikipedia.org/wiki/W._Richard_Stevens](http://en.wikipedia.org/wiki/W._Richard_Stevens)

1998 - UNIX Network Programming, Volume 1, Second Edition: Networking APIs: Sockets and XTI - ISBN 0-13-490012-X

1999 - UNIX Network Programming, Volume 2, Second Edition: Interprocess Communications - ISBN 0-13-081081-9

2003 - UNIX Network Programming Volume 1, Third Edition: The Sockets Networking API - ISBN 0-13-141155-1 (with Bill Fenner, and Andrew M. Rudoff)

2005 - Advanced Programming in the UNIX Environment, Second Edition - ISBN 0-32-152594-9 (with Stephen A. Rago)

---

### Post by quip on 2009-12-18
I second the Beej guide, only because I have used it myself and found it to be quite good (at least the parts I looked at..)

One more thing to the OP:  unless you already have a very thorough understanding of networking in general, you probably ought to start at something simpler and more abstract than packet inspection if you really want to understand network programming.

---

### Post by kwyto on 2009-12-18
hi guys, 
for packet inspection I think wireshark is one of the best, free and easy to use.  
for programming, I would recommend first getting familiar with C, writing your a couple of programs using different types of sockets, its important to understand what's TCP, UDP, different protocols, etc. It's no simple matter but with dedication you can mastered. good luck!!!!

---

### Post by ApEkV2 on 2009-12-18
Awesome, it's going to take a while for me to read it (and buy the books).
Thanks for the quick replies, looks like I will have something to do over Christmas after all.

@ quip, I wouldn't consider myself having a thorough knowledge in networking, but then again what is your definition of thorough?
My thinking is, next semester in college, these books (and guide) will fit right in with the courses I'm taking.

---

### Post by kwyto on 2009-12-18
be careful with those courses, a lot of teachers like the theoretical approach, instead of the practical or a combination of both. i recommend that before you sign up for a class ask your professor for the syllabus, and also what is he planning to do in the class, it will save a lot of time and disappointments. i took a network class which turned out to be all theory and no programming, complete waste of my time. well, not complete but ...... do research 

feel the water before jumping in

---

### Post by quip on 2009-12-18
> **ApEkV2 said:**
> Awesome, it's going to take a while for me to read it (and buy the books).
Thanks for the quick replies, looks like I will have something to do over Christmas after all.

@ quip, I wouldn't consider myself having a thorough knowledge in networking, but then again what is your definition of thorough?
My thinking is, next semester in college, these books (and guide) will fit right in with the courses I'm taking.

Depends on what your goals are, and what classes you are taking.  If they are for a CS degree at a university, there will be a lot of theory.  The theory can get boring, but it is the theory that led to the code.

On what I meant by thorough:  you feel confident and can write (in a reasonable amount of time) code that does socket programming, accepting requests from the network to process, and then sending them back; a knowledge of OSI and TCP/IP models, including layer definitions and functions; the difference between a packet and a frame, and maybe some routing and switching knowledge.  Basically what you should have when you complete the books and/or the course.  ;)

---

### Post by StunnerAlpha on 2009-12-19
Don't think that learning theory is a bad thing though since you can't do anything without theory. You need an idea before you can write any (useful) code since theory is what leads to the code, as the poster above me stated. My point: theory is extremely important so don't underestimate it. If you fully understand the theory behind something you will understand it sooooo much better than someone who learned by looking at coding examples.

---

### Post by kwyto on 2009-12-19
you guys are right. theory is very important, but many teachers take a theoretical approach to a class because they can't do any practical. i think a good mix of both its the best way to do it. the problem is that is hard to find a good theory guy that is good at practical stuff. practice requires a lot of your time, stresses the importance of emerging yourself in code, which undoubtly leaves you with little time for theory. its takes time and dedication to achieve a balance of both, theory and practice

---

