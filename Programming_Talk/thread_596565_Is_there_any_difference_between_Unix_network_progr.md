---
title: "Is there any difference between Unix network programming and Linux network programmin"
date: 2007-10-29
forum: Programming Talk
---

### Post by fyplinux on 2007-10-29
HI, 

I found a book named <unix network programming>, but I am working under Ubuntu, I am wondering whether this book could guide me to program in Ubuntu?

Is there any difference between Unix network programming and Linux network programming? if so, does that mean I cannot use this book?

Regards.

---

### Post by Chickencha on 2007-10-30
Short answer: yes, the book is probably fine.

Long answer: I'm no expert on the subject of network programming, but in general any programming resource that says it applies to Unix will also apply to Linux.  There are probably some exceptions (and you'd have to look up the specifics of what they are), but usually you can assume compatibility.  I wouldn't be too surprised if the topic is addressed in the book somewhere.  You might take a look.

---

### Post by dwhitney67 on 2007-10-30
I recall (in the ol' days) that under Solaris I had to link C/C++ programs with the socket library; under Linux I do not.  Hence the reason why Makefiles (and configuration scripts) are useful.

---

### Post by slavik on 2007-10-30
Don't take the information in the book for granted, double check on it through man pages.

example:
bzero is deprecated in Linux (might not be there anymore at all), not so on Solaris.

---

### Post by fyplinux on 2007-10-30
This book introduces Berkeley Sockets, which is the same architecture with Linux. From this point, it might be a guideline, in fact, I found the content is similar to the man page.

---

### Post by slavik on 2007-10-30
I'm just saying that you should double check some stuff when coding. A professor told me that when she was teaching Unix workstation programming, they used Solaris systems and wanted to try out Linux. The Linux version of the code didn't work at all, because most of the system calls were stubs (returned successfully but didn't do anything). This was in 1995.

---

### Post by AlexThomson_NZ on 2007-10-30
I'm not sure how useful the book is off-hand- I am sure a lot of the theory and terminology is right, but as has been mentioned, some of the implementation may have changed over time.  Luckily, Linux network programming is well documented on the www, and there are lots of simple tutorials, etc. to follow.

Here's a good starting point: [http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

---

### Post by KCPokes on 2007-10-30
Take a look at the copyright of the book.  If the book is older, then keep an open mind that the fundamentals may be the same but the implementation of said fundamentals may have changed.  Much is going to be determined at what level you are diving into.  Basic IP configuration, conceptually, hasn't changed in years, but commands/utilities tend to deprecate and change.

---

### Post by slavik on 2007-10-30
> **KCPokes said:**
> Take a look at the copyright of the book.  If the book is older, then keep an open mind that the fundamentals may be the same but the implementation of said fundamentals may have changed.  Much is going to be determined at what level you are diving into.  Basic IP configuration, conceptually, hasn't changed in years, but commands/utilities tend to deprecate and change.
and order of arguments ;)

---

