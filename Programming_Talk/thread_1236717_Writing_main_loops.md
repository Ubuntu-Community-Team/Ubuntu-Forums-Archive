---
title: "Writing main loops"
date: 2009-08-10
forum: Programming Talk
---

### Post by JustAnotherVagueAnon on 2009-08-10
I want to write a main loop that is able to idle such as glutMainLoop() from OpenGL and various others. I want this loop to wait for input rather than entering a plain old infinite loop. I have an idea this may have to do with threading, a topic I am not yet knowledgeable of, so I am looking for a step in the right direction and I would like to write this in C.

---

### Post by dwhitney67 on 2009-08-10
It depends on what type of input you are looking at; if it is merely standard-input, or input from a socket, then a select() or poll() can be used.  There's also pselect() and ppoll().

For obtaining X (ie mouse) events, you will need to reference the toolkit that you are using, for this varies from one to the next.  Conceptually, though, the same principles apply.

P.S.  Multi-threading is a different topic altogether.  Single-threaded apps can use the polling ideas given above.

---

### Post by lisati on 2009-08-10
I was taught that an infinite loop is a bad idea, and that you should give some thought to the circumstances in which the loop should stop.

---

### Post by dwhitney67 on 2009-08-10
> **lisati said:**
> I was taught that an infinite loop is a bad idea, and that you should give some thought to the circumstances in which the loop should stop.

Good advice.

A friend from long ago, who at the time worked for a well-known Silicon Valley company (the name has the letters H and P in it), had a manager that stated that the company wants to ensure that it delivers software without any bugs.

Now, for those in the s/w industry and with a cynical mind would reply "No sh*t sherlock".

I guess the same could be said about your mentor.

---

### Post by JustAnotherVagueAnon on 2009-08-10
Thanks both. ppoll seems to be just what I was looking for. Just out of curiosity, what does the code for these functions look like? I couldn't locate the source but I'm interested in knowing what concepts are used in the functions that allow the computer to be able to idle like that.

---

### Post by stroyan on 2009-08-10
That function call is implemented in libc as a system call.
The process tells the kernel to no longer schedule it to run until some condition occurs.
You can read about the kernel scheduling implementation at
[http://oreilly.com/catalog/linuxkernel/chapter/ch10.html](http://oreilly.com/catalog/linuxkernel/chapter/ch10.html)

(But the scheduler has been overhauled since then.  See [http://en.wikipedia.org/wiki/Completely_Fair_Scheduler](http://en.wikipedia.org/wiki/Completely_Fair_Scheduler) for the latest version.)

---

