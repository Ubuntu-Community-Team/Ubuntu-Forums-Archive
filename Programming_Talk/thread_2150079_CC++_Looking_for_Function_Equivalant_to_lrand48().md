---
title: "C/C++: Looking for Function Equivalant to lrand48()"
date: 2013-05-30
forum: Programming Talk
---

### Post by AntumDeluge on 2013-05-30
I've got a piece of source code that I'm trying to port to Windows. The code makes use of the Linux/Unix function [COLOR=red]lrand48()[/COLOR]. I'm trying to find or create a similar function that can be used for Windows code without the use of an external library (e.g. boost, OpenEXR):

[php]#if defined(WIN32) || defined(WIN64)
#define _LRAND48() rand()
#else
#define _LRAND48() lrand48()
#endif[/php]

I know that [COLOR=red]rand()[/COLOR] is not uniform alone. What I understand about [COLOR=red]lrand48()[/COLOR] is that it returns a 48-bit unsigned long integer.

**----- EDIT -----**

I said "C/C++" in the title, but it's actually a C project.

---

### Post by trent.josephsen on 2013-05-30
Did your post have a question?

I'd never heard of lrand48 before, so I looked it up. Turns out it's a Sys V extension that has been deprecated since 1986 according to lrand48(3) and Wikipedia. That's older than the oldest C standard. How old is this code you're trying to port?

From reading the man page, lrand48() should be no more uniform than a typical implementation of rand(), and less so than some. Although I admit I'm not sure how to prove anything about the formula's distribution... that's a task for a better mathematician than me.

---

### Post by AntumDeluge on 2013-05-31
Thank you, that's actually pretty informative. I'll just leave the rand() code for now unless the devs reply to an email I sent.

---

