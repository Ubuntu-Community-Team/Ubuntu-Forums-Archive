---
title: "scanf timeout"
date: 2006-09-07
forum: Programming Talk
---

### Post by richardhp on 2006-09-07
Ok I have read a solution on Google for this on windows but I didn't understand it and it did not compile.

What I wanted to do write a program that waited for the user to input some data, but time-out if they waited too long. This is part of a maths game where the user is asked maths questions but they only have a limited amount of time to answer the question.

My problem is, it waits infinitely before the counter starts, I wondered if there was a way of cutting short the scanf function and continuing with the rest of the program if they did not enter any data

---

### Post by richardhp on 2006-09-09
Ok well all I have found so far is this:


Hello All!
>
> I want to ask you whether there is any way to check asynchronously
> whether stdin contain data to read. I tried all operations to read
> stdin, but it looks all that operations are blocking.
>

There is no way to check that in standard C++ (or C). But your platform may
provide a non-standard way to do this.

john

Which does not bode well for me.

The only other possible solution I can think of is to have some kind of loop that stops when a key is pressed but I don't know how to do this without writing an assembly routine to do it for me.

Has anyone got any ideas?

---

### Post by nereid on 2006-09-09
Have you tried threads? Start a second thread before the scanf and let this one time out after for example 5 seconds than terminate with this one the scanf input (I don't know if this works but this was the first thing that came to my mind).

---

### Post by richardhp on 2006-09-16
Ok thanks, I don't know much about threads, but I have managed to come up with a similar solution that I found on the internet.

It involves using the alarm(int n) funtion included in signals.h

It sets a timer that sends an interrupt signal after n seconds. You can then write a function that handles the signal for you which in my case was to do something other than wait for user input.

---

### Post by scourge on 2006-09-16
Sticking with pure ANSI C code is a nice plan, but often an impossible one. I would probably just use the non-blocking read functions in unistd. Using an interrupt signal doesn't sound like a clean solution to me.

---

### Post by -Rick- on 2006-09-16
You can use [select]("http://unixhelp.ed.ac.uk/CGI/man-cgi?select+2") or [poll]("http://bama.ua.edu/cgi-bin/man-cgi?poll+2") to check if stdin has input(and set a max timeout for checking).

---

### Post by richardhp on 2006-10-15
cheers guys,

i will look into these. you were right, using the alarm function was very messy indeed.

---

### Post by amo-ej1 on 2006-10-16
I'm surprised it took so long for people to suggest select() which would've been my first choice

---

