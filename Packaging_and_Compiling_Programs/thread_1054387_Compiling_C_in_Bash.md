---
title: "Compiling C in Bash"
date: 2009-01-29
forum: Packaging and Compiling Programs
---

### Post by richanderson1984 on 2009-01-29
I'm new to both programming and Linux, so please bear with me. I've started off with C, and have been compiling using the following command:

gcc -o filename filename.c

However, when I input the gets() function into source code, I receive the following warning message from Ubuntu:

filename.c:(.text+0x54): warning: the 'gets' function is dangerous and should not be used.

How do I bypass this warning message? Any help would be much appreciated.

Thanks,
Richard

---

### Post by cmay on 2009-01-29
i would heed the warning and start using fgets instead. here is a link to the description of it. gets is not so good  as it can course bufferoverflows pretty easy. [http://www.cplusplus.com/reference/clibrary/cstdio/fgets.html](http://www.cplusplus.com/reference/clibrary/cstdio/fgets.html)

its been a while since i did any c last so i may remember wrong but i am sure gets is not safe to use anyhow. 
good luck to you.

---

### Post by richanderson1984 on 2009-01-29
Thanks, this worked like a treat :)

---

### Post by cmay on 2009-01-29
no problem . glad to help and welcome to the forums by the way .

---

### Post by Tek-E on 2009-02-19
> **cmay said:**
> no problem . glad to help and welcome to the forums by the way .

Doesnt gets() leave a greater possibility for the chance of a buffer overflow?

---

