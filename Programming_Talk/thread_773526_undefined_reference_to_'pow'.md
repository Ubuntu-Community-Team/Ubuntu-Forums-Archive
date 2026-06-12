---
title: "undefined reference to 'pow'"
date: 2008-04-28
forum: Programming Talk
---

### Post by jon zendatta on 2008-04-28
hell0 people

doing some simple C..but some problems with the math functions even though i am using the math header --           #include <stdio.h>
                                      #include <math.h>
problem being it will not compile! :KS
ps:sorry i probably should be posting this in the absolute beginner's forum

---

### Post by LaRoza on 2008-04-28
> **jon zendatta said:**
> hell0 people

doing some simple C..but some problems with the math functions even though i am using the math header --           #include <stdio.h>
                                      #include <math.h>
problem being it will not compile! :KS
ps:sorry i probably should be posting this in the absolute beginner's forum

Add this:

```

gcc -lm 

```

And whatever else you use, just make sure to have -lm.

---

### Post by jon zendatta on 2008-04-28
cheers 
so is this how i compile?

gcc -lm file file.c

---

### Post by dwhitney67 on 2008-04-29
You should read the man-pages!
```
$ man gcc
$ man pow
```

To compile:
```
$ gcc -o myFile myFile.c -lm
```

Don't name your executable 'file', because a binary with that name already exists in /usr/bin.

(The -lm does not have to be at the end; that's just my preference.)

---

### Post by jon zendatta on 2008-04-29
thank you lar0za/dwhitney67
that works good,  linux rules:KS

---

### Post by roho@Lenovo on 2011-11-14
-lm being at the end or at the start makes a diference to the linker. Don't know why

---

### Post by gavin_attoe on 2011-11-14
> **dwhitney67 said:**
> 
(The -lm does not have to be at the end; that's just my preference.)

Well it looks like this is pretty well all solved.  I just thought I'd add my preferred placement of -lm as the innards of a sandwich of file names.

```
$ cc myFile.c -lm -o myFile.out
```

Yummy.

---

### Post by schauerlich on 2011-11-15
> **roho@Lenovo said:**
> -lm being at the end or at the start makes a diference to the linker. Don't know why

[s]I don't believe it should. Most likely, placing it at the beginning or end is inadvertently interfering with another flag.[/s]

disregard that, i'm wrong.

---

### Post by MadCow108 on 2011-11-15
> **schauerlich said:**
> I don't believe it should. Most likely, placing it at the beginning or end is inadvertently interfering with another flag.

it does.
this is always the case with static libraries and also for shared libraries when linking with --as-needed (now default in ubuntu).
gcc handles its commandline from left to right and references must be registered before they are provided.

---

### Post by schauerlich on 2011-11-15
> **MadCow108 said:**
> it does.
this is always the case with static libraries and also for shared libraries when linking with --as-needed (now default in ubuntu).
gcc handles its commandline from left to right and references must be registered before they are provided.

Well, shows how much I know. :)

---

