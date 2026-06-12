---
title: "What is the maximum length of a username?"
date: 2007-06-22
forum: Programming Talk
---

### Post by ConCor on 2007-06-22
Hello,

For a small program I'm writing, I need to store the username of the user who executed the program. I know what functions to use to get at the username, but I don't know how much space to allocate to the character array.

The manual for glibc says that a macro L_cuserid in <stdio.h> can be used to determine the number of characters necessary to store a username returned by cuserid(). I'm not using cuserid(), as the glibc site states that that function is deprecated.

In <bits/utmp.h> (included through <utmp.h>), there is a macro UT_NAMESIZE defined, which is used to set the length of field ut_user in struct utmp.

What is the actual maximum length of a username (not just in Ubuntu, but Linux in general)? L_cuserid is defined on my system to be 8. UT_NAMESIZE is defined to be 32. Which should I use? Or, should I use another value entirely?

Thanks in advance,

Conor

---

### Post by batrick on 2007-06-22
I would assume you wouldn't need to set the size like that. You just need to read the username and use strlen() to find out how big it is. Then use malloc() to allocate space for it.

---

