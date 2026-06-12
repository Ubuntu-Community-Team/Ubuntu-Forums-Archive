---
title: "Linux equivalent of int 10h"
date: 2008-05-10
forum: Programming Talk
---

### Post by Chicken Dinner on 2008-05-10
I have a quick question regarding assembly programming and Linux.

Is there a similar system call, in Linux, to Windows'/DOS' interrupt 10h, or VIDEO service?
Thank you.

---

### Post by stroyan on 2008-05-10
The closest match is writing characters to stdout, (file descriptor 1).
See [http://asm.sourceforge.net/articles/linasm.html](http://asm.sourceforge.net/articles/linasm.html) and the
"hello world" example in that page.

---

### Post by slavik on 2008-05-11
DOS has 21h and 10h, Linux has only 80h.

There are also guides out that list all kernel calls, how to put arguments in and such.

---

