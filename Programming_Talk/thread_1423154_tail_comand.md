---
title: "tail comand"
date: 2010-03-06
forum: Programming Talk
---

### Post by vksingh on 2010-03-06
Hi,

I tried the following command but it did not work.

**[COLOR=Black]tail -2 test2 [/COLOR]**

Please help.

Thanks,

Vivek

---

### Post by vksingh on 2010-03-06
Hi,
I tried tail command like the following:

tail +7 test.txt.

But its is printing the whole content of the file. Please help.


Thanks,

Vivek

---

### Post by matmatmat on 2010-03-06
Are you trying to print out the last two lines? If so it it -n 2

---

### Post by MadCow108 on 2010-03-06
you still need the -n

tail -n +5 text
or
tail --lines=+5 text

---

### Post by Sef on 2010-03-06
Merged duplicate threads.

---

