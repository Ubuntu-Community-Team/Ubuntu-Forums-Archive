---
title: "A function to see if the string provided is a path in C"
date: 2009-01-16
forum: Programming Talk
---

### Post by PmDematagoda on 2009-01-16
I was wondering if there was a function that checked the string provided to it to see if it was a path or just a string, I tried using access(), however the effect I wanted did not seem to be there, a big part of this probably because I couldn't find any documentation by googling access().

Any help on this is appreciated:).

---

### Post by eye208 on 2009-01-16
> **PmDematagoda said:**
> I couldn't find any documentation by googling access().
sudo apt-get install manpages-dev
man access

or just see here:
[http://www.opengroup.org/onlinepubs/000095399/functions/access.html](http://www.opengroup.org/onlinepubs/000095399/functions/access.html)

---

### Post by dwhitney67 on 2009-01-16
I read the man-page on access(), and found the following paragraph interesting:
```

       Warning:  Using  access()  to check if a user is authorized to, for example, open a
       file before actually doing so using open(2) creates a security  hole,  because  the
       user might exploit the short time interval between checking and opening the file to
       manipulate it.  For this reason, the use of this system call should be avoided.

```

If you need to verify if a path is valid, consider using stat().  It will return whether the path is valid or not; if valid, then you can also check the st_mode field within the stat buffer structure to determine if the path is a directory, a regular file, or something else.

---

### Post by PmDematagoda on 2009-01-16
Thanks for the tip on stat() and the man-pages, I was already looking for the access() function on man, however I think I didn't have the necessary package at the time:).

---

