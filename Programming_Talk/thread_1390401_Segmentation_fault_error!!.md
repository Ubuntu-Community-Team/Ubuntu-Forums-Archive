---
title: "Segmentation fault error!!"
date: 2010-01-25
forum: Programming Talk
---

### Post by K-Z on 2010-01-25
Done...

---

### Post by lisati on 2010-01-25
First thought: is the fopen() working?

---

### Post by dwhitney67 on 2010-01-25
This little puppy needs to point to some valid memory location within the program space; not just dangle.
```

char *lgfle1;

```

---

### Post by K-Z on 2010-01-26
> **lisati said:**
> First thought: is the fopen() working?
  yup....tht has been tested...

---

### Post by K-Z on 2010-01-26
> **dwhitney67 said:**
> This little puppy needs to point to some valid memory location within the program space; not just dangle.
```

char *lgfle1;

```
lgfle is the logfile containing output of netstat -p command that would be passed from the shell...

---

### Post by dwhitney67 on 2010-01-26
> **K-Z said:**
> lgfle is the logfile containing output of netstat -p command that would be passed from the shell...

It's use in the fscanf() is causing your app to "barf".

---

### Post by ibuclaw on 2010-01-26
> **K-Z said:**
> lgfle is the logfile containing output of netstat -p command that would be passed from the shell...

What dwhitney means is that lgfle1 = (null);

fscanf() runs successfully, but never passes any data to lgfile1 because it is not pointing to any memory.

edit:
Also, correct me if I'm wrong, but wouldn't fscanf only return the first word in the logfile? As it should stop after the first bit of whitespace is found.

Regards
Iain

---

### Post by dwhitney67 on 2010-01-26
> **tinivole said:**
> What dwhitney means is that lgfle1 = (null);

There's no guarantee that this is the case; lgfle1 could be pointing anywhere.  I bet it's pointing to an address (perhaps 0x00) that's outside the program space, thus causing the app to crash.

---

### Post by K-Z on 2010-01-28
I have sorted out the problem. Actually we would have to use fgetc instead of fscanf to store complete data of file in lgfle.

---

