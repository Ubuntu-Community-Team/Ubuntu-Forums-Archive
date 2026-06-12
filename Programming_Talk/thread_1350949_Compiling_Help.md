---
title: "Compiling Help"
date: 2009-12-09
forum: Programming Talk
---

### Post by spikoley on 2009-12-09
I need help compiling a program to access a router.  The files and directions are [here]("http://www.seattlewireless.net/telnetenable.c").  The directions aren't detailed and I need assistance.  Thanks.

> To build this code on Un*x, first download a copy of the MD5 and Blowfish .c AND .h files from [http://www.opentom.org/Mkttimage](http://www.opentom.org/Mkttimage)

I've to add

#include <stdio.h>

#include <string.h>

to md5.c

When compiling on FreeBSD you may get errors about tcp.h. You will need to add:

#include <sys/types.h>

to telnetenable.c. It will compile with warnings, but it will run perfectly after that.

Then compile using GCC as follows:

gcc -o telnetenable md5.c blowfish.c telnetenable.c

(I had to replace PORT with 23 to compile)

---

### Post by MadCow108 on 2009-12-10
whats the problem?
have you even tried?

---

### Post by spikoley on 2009-12-10
Yes, I did try and kept receiving errors.  I used another distro to get it working.  There is something about Ubuntu that won't let it compile.  Consider this thread closed and thanks for the reply.

---

### Post by Physical Hook on 2009-12-10
What errors ?

---

### Post by spikoley on 2009-12-11
> **Physical Hook said:**
> What errors ?

I got it working with another distro.  Thanks for the reply.

---

### Post by lisati on 2009-12-11
> **spikoley said:**
> I got it working with another distro.  Thanks for the reply.

What errors? [Why isn't this thread marked "Solved"?]("http://lmgtfy.com/?q=mark+thread+solved+site:ubuntuforums.org") Did you install "build-essential"?

---

### Post by spikoley on 2009-12-13
> **lisati said:**
> What errors? [Why isn't this thread marked "Solved"?]("http://lmgtfy.com/?q=mark+thread+solved+site:ubuntuforums.org") Did you install "build-essential"?

It doesn't work with Ubuntu and others have confirmed.  

This thread isn't marked solved because there is no solution here.  The whole point of marking a thread solved is so when you are searching for a solution you know where to look.  Why would you mark a thread solved if there is no solution in it?

---

### Post by MadCow108 on 2009-12-13
how should it be solved if you haven't even described the problem.

"It doesn't work" is no adequate description.

---

### Post by lisati on 2009-12-13
> **spikoley said:**
> It doesn't work with Ubuntu and others have confirmed.  

This thread isn't marked solved because there is no solution here.  The whole point of marking a thread solved is so when you are searching for a solution you know where to look.  Why would you mark a thread solved if there is no solution in it?

Why would you waste our time if you know there is no solution here and you know where to find the answer?

Please answer the questions of those who have tried to help you otherwise you will be dismissed as a troll.

[LIST=1]
[*]What error messages did you get? "I got it working with another distro" isn't an answer.
[*]Have you installed the build-essential package?
[/LIST]

---

### Post by Physical Hook on 2009-12-13
Indeed, you are a troll. I just compiled it and it works like a charm.

> **spikoley said:**
> It doesn't work with Ubuntu and others have confirmed.  

Who are 'others' ? No one have confirmed this fact here.

---

### Post by Physical Hook on 2009-12-13
Download attached file ( modified ), extract it and compile:

```
make
gcc md5.c blowfish.c telnetenable.c -o telnetenable
```

---

