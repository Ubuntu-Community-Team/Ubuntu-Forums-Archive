---
title: "where is setsockopt implemented"
date: 2010-10-24
forum: Programming Talk
---

### Post by jamesbon on 2010-10-24
Where is setsockopt defined 
I looked in /usr/include/sys/socket.h

```
extern int setsockopt (int __fd, int __level, int __optname,
                       __const void *__optval, socklen_t __optlen) __THROW;

```
I am searching for place where this is implemented in file
/usr/include/sys/socket.h
there was nothing more than the above definition.

---

### Post by worseisworser on 2010-10-24
[http://lxr.linux.no/linux+v2.6.36/net/core/sock.c#L480](http://lxr.linux.no/linux+v2.6.36/net/core/sock.c#L480)   etc.

The kernel source is available via the repositories by the way.

---

### Post by dwhitney67 on 2010-10-24
Hee hee... looks I posted in haste.  Oh where could it be *implemented*...

---

### Post by worseisworser on 2010-10-24
edit: ..right..

---

### Post by jamesbon on 2010-10-25
The link you gave is about sock_setsockopt
where as I am looking for setsockopt
are these both same.
My idea was when a function is defined then it must have its definition some where in /usr/include that is how I make my functions and headers is that not the case with these system calls.

---

### Post by dwhitney67 on 2010-10-25
worseisworser was correct; the function you seek is implemented in the kernel.

The C library, which you use to call setsockopt(), calls the kernel equivalent.

---

### Post by jamesbon on 2010-10-25
> **dwhitney67 said:**
> worseisworser was correct; the function you seek is implemented in the kernel.
I am not able to understand this you mean to say sock_setsockopt is kernel equivalent of setsockopt
> **dwhitney67 said:**
> 
The C library, which you use to call setsockopt(), calls the kernel equivalent.
Are you referring to sys/types.h or sys/socket.h

---

### Post by dwhitney67 on 2010-10-25
> **jamesbon said:**
> I am not able to understand this you mean to say sock_setsockopt is kernel equivalent of setsockopt

Are you referring to sys/types.h or sys/socket.h

Think of setsockopt() as a wrapper function around sock_setsockopt().  Thus don't treat sock_setsockopt() as something you would call directly from a C or C++ application.

As for your second question, setsockopt() is declared in sys/socket.h.  It is implemented in the C library (libc.so), and this function calls the sock_setsockopt() function that is declared/implemented in the kernel.

---

