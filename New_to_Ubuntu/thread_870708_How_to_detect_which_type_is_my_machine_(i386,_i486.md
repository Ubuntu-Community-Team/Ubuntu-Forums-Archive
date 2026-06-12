---
title: "How to detect which type is my machine (i386, i486, i586...)"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by RuleMaker on 2008-07-26
As I asked in the title, do I detect that, i think I have currently installed i386 ubuntu 8.04, does that matter and do I have to install the same type as my machine is?

---

### Post by Bachstelze on 2008-07-26
Wikipedia is your friend, but why does it matter? There is no i486, i586 or i686 Ubuntu.

---

### Post by Sef on 2008-07-26
> As I asked in the title, do I detect that, i think I have currently installed i386 ubuntu 8.04, does that matter and do I have to install the same type as my machine is?


It doesn't matter.  What matters is if you have a 32-bit or 64-bit system.  A 32-bit can only install a 32-bit operating system, while a 64-bit system can install a 32 or 64-bit one.

---

### Post by Bachstelze on 2008-07-26
> **Sef said:**
> while a 64-bit system can install a 32 or 64-bit one.

Not *any* 64 bit system can, though. The AMD64/EM64T architectures are hybrid archs that are backwards-compatible with 32 bit code, but not all 64 bit architectures are.

---

### Post by sdennie on 2008-07-26
> **HymnToLife said:**
> Wikipedia is your friend, but why does it matter? There is no i486, i586 or i686 Ubuntu.

That's not completely true.  ;)

There is a -386 kernel in Hardy (though, it's compiled with 486 optimizations) and it doesn't support SMP among other things.

> 
As I asked in the title, do I detect that, i think I have currently installed i386 ubuntu 8.04, does that matter and do I have to install the same type as my machine is?


To see what kernel you are using, try:

```

uname -r

```

If it ends in -386, you probably don't want to be using that kernel but instead the kernel that ends in -generic.

To find out what CPU your machine is using try:

```

grep "model name" /proc/cpuinfo

```

---

### Post by RuleMaker on 2008-07-26
Thank you all for answering my question!

---

### Post by Bachstelze on 2008-07-26
> **vor said:**
> That's not completely true.  ;)

There is a -386 kernel in Hardy (though, it's compiled with 486 optimizations) and it doesn't support SMP among other things.

Right. All other binaries, though, are labeled i386, and the same goes for the CD images.

---

