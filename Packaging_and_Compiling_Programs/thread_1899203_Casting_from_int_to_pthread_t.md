---
title: "Casting from int to pthread_t"
date: 2011-12-23
forum: Packaging and Compiling Programs
---

### Post by dodle on 2011-12-23
I'm trying to compile libxml2 for MinGW for my Windows machine. But I get an error during compilation:

```
error: conversion to non-scalar type requested
```

This is the line:
```
tid[i] = (pthread_t) -1;
```

I recently read a comment that states that version 4 of gcc has a problem with this type of cast. Has anyone heard the same? I am using 4.6.1. Is there some kind of hack that I can do? I don't think there is a newer version available for MinGW yet. I'll try compiling it with v3.4 and see if it works.

**----- EDIT -----**

Nope, same problem with 3.4.5. If I get around to it I'll try to compile on Ubuntu. Don't Natty and Oneiric use version 4-something by default?

**----- EDIT -----**

I disabled threads (--without-threads) for now to get it to compile. Maybe the problem is with the version of pthreads that I have installed.

---

### Post by Bachstelze on 2011-12-23
What makes you think that pthread_t and int are compatible types?

*EDIT:* More precisely:

[http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/sys_types.h.html](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/sys_types.h.html)

> 
IEEE Std 1003.1-2001/Cor 2-2004, item XBD/TC2/D6/26 is applied, adding pthread_t to the list of types that are not required to be arithmetic types, **thus allowing pthread_t to be defined as a structure**.

---

### Post by dodle on 2011-12-23
[quote=Bachstelze]What makes you think that pthread_t and int are compatible types?[/quote]

I don't know, I just downloaded this source for the libxml2 library and was trying to compile it.

---

### Post by Bachstelze on 2011-12-23
> **dodle said:**
> I don't know, I just downloaded this source for the libxml2 library and was trying to compile it.

Well, that's a bug in the code, then. :)

---

