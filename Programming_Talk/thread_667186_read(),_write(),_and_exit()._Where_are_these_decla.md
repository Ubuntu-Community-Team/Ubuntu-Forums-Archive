---
title: "read(), write(), and exit(). Where are these declared?"
date: 2008-01-14
forum: Programming Talk
---

### Post by ZDemon on 2008-01-14
Hi.

Just an idiot question:

read(), write(), and exit(). Where are these declared?

Where is the header file that declares these functions?

Also, can someone teach me how to look for it myself.

Thanks

---

### Post by amo-ej1 on 2008-01-14
sure, start by installing the development manpages  by typing sudo apt-get install manpages-dev 

Then  you can simply type man read or man write or man exit 


There you can clearly read the following 
```

NAME
       read - read from a file descriptor

SYNOPSIS
       #include <unistd.h>

       ssize_t read(int fd, void *buf, size_t count);

DESCRIPTION
       read()  attempts to read up to count bytes from file descriptor fd into
       the buffer starting at buf.

```

---

### Post by fyplinux on 2008-01-14
I recommend a website to look up these stuff:

[http://linux.die.net/man/3/popen](http://linux.die.net/man/3/popen)

The best seachable manual I found!

---

### Post by ZDemon on 2008-01-15
Wow, i didnt know it was so easy. Linux is great.

Thats great guys. Thanks for helping out a newbie.

---

