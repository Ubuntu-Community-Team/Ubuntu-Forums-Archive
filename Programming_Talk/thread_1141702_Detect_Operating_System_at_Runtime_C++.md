---
title: "Detect Operating System at Runtime C++"
date: 2009-04-28
forum: Programming Talk
---

### Post by camper365 on 2009-04-28
Is there a function that I can call that would allow detection of the Operating System at runtime?
What I would want would be to determine the version of the Linux kernel and other system stats at runtime. I would then log this info to a text file.

---

### Post by Anthon on 2009-04-28
uname -a 
gives you that information from the commandline.
There is also a system call uname ( do 
  man 2 uname
for information). You should be able to call that one from C++

---

### Post by Christmas on 2009-04-28
Maybe try something like *system ("uname -a");* or *system ("cat /etc/debian_version >somefile");*

---

### Post by happysmileman on 2009-04-28
```
#include <sys/utsname.h>

int uname(struct utsname *buf);

returns pointer to a utsname:

struct utsname {
    char sysname[];    /* Operating system name (e.g., "Linux") */
    char nodename[];   /* Name within "some implementation-defined
                                     network" */
    char release[];    /* OS release (e.g., "2.6.28") */
    char version[];    /* OS version */
    char machine[];    /* Hardware identifier */
#ifdef _GNU_SOURCE
    char domainname[]; /* NIS or YP domain name */
#endif
};
```

---

