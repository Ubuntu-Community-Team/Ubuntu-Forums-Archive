---
title: "Is python really ideal for making applications?"
date: 2008-07-17
forum: Programming Talk
---

### Post by Exershio on 2008-07-17
I ask this question because I've noticed one thing while using Exaile, which was written in python. It's slow as hell. Resizing the window is considerably laggy compared to other applications written in C.

So is Python really good for applications and Exaile is just slow because of being poorly written?

I'm asking this because I'm really interested in Python. It's such a beautiful language, but I don't want to write a program that will lag on your everyday Pentium 4 with 2 gigs of ram.

---

### Post by bruce89 on 2008-07-17
> **Exershio said:**
> So is Python really good for applications and Exaile is just slow because of being poorly written?

I think it's a combination. Python programs will always be slower than C ones, but maybe Exaile is badly written.

Looking at it myself, it doesn't seem to be any slower than usual, perhaps it's the complex UI that does it.

---

### Post by sonofusion82 on 2008-07-17
yes, Python should be slower than C/C++ programs.
but in your case, I believe that resizing UI should not be due to the python code, resizing is typically more dependent on the undelying GTK+ unless it has a great deal of custom widgets written in python

---

### Post by LaRoza on 2008-07-17
> **Exershio said:**
> I ask this question because I've noticed one thing while using Exaile, which was written in python. It's slow as hell. Resizing the window is considerably laggy compared to other applications written in C.

Probably a WM or the apps fault.

> 
So is Python really good for applications and Exaile is just slow because of being poorly written?
Windows is slow, does that mean C is slow (or C++)?

> 
I'm asking this because I'm really interested in Python. It's such a beautiful language, but I don't want to write a program that will lag on your everyday Pentium 4 with 2 gigs of ram.
No, Python is good enough for the Ubuntu installer for Ubuntu development ;)

---

### Post by slavik on 2008-07-17
python is not ideal, nothing is ever ideal ... :)

---

### Post by pmasiar on 2008-07-17
> **Exershio said:**
> So is Python really good for applications and Exaile is just slow because of being poorly written?

Most likely. 

Python is excellent choice for wide range of applications, and for couple of reasons:
- many tasks are limited not by CPU numbercrunching power, but I/O bandwidth, database query delay, server response and such. For those tasks, Python is excellent choice (including GUI, where most time program idles, waiting for response)
- Python design allows for developing app, then finding the bottleneck, and recoding **only that 5% of the code** as fast C library.

Of course Python is not "silver bullet" and other languages might be better choice for different reasons, one of them might be compatibility or legacy: that's the reason why people still maintain 40 years old COBOL code.

There are many programmer without real-life experience obsessed with raw speed of C (we call them here 'speed kiddies'). In real life, most important speed it 'speed to market' (or meet deadline to make your boss happy/match competitor's features).

---

### Post by Kiefer Rodriguez on 2008-07-18
> **pmasiar said:**
>  
There are many programmer without real-life experience obsessed with raw speed of C (we call them here 'speed kiddies'). In real life, most important speed it 'speed to market' (or meet deadline to make your boss happy/match competitor's features).

I couldn't agree more with you *pmasair*, so called '*speed-kiddies*' will fuss over C's raw speed, but don't begin to consider that C may not be suitable for the project at hand, the truth is that yes, *Python* is a beautiful language and is viable for large programs, ever heard of a little thing called *YouTube*? or a small company named *NASA*? ;-)

~***Kiefer***

---

