---
title: "what is &quot;tchar.h&quot; equvalent in linux?"
date: 2010-06-28
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-28
Hi All,

I wish to port a win32 application to linux platform. 
I wanted to know if there is any equivalent of tchar.h in linux platform?

Thanks in advance.

---

### Post by Milliways on 2010-06-28
> **jeremy28 said:**
> Hi All,

I wish to port a win32 application to linux platform. 
I wanted to know if there is any equivalent of tchar.h in linux platform?

Thanks in advance.

tchar.h is just a set of macros to select different strings/functions for Unicode/8 bit characters, and is MicroSoft specific.

There is no equivalent, because Unicode is handled differently in Linux (usually UTF-8 )

Mind you, this is going to be the least of your problems, because unless it is a very simple console application you will need to change most of the API calls.

---

