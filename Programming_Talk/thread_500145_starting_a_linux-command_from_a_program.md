---
title: "starting a linux-command from a program"
date: 2007-07-13
forum: Programming Talk
---

### Post by Golly on 2007-07-13
Hello,
I try to start APT from my program.
And compute the exit-code from this call in my program.

So I use ```
int erg = system("apt-get update");
```
When I start my program, the system-call running, but
the computer hangup after a view output-lines from APT.

What is wrong with my call?

Bye Golly

---

### Post by Wybiral on 2007-07-13
Try:

```

int erg = system("sudo apt-get update");

```

---

### Post by Golly on 2007-07-14
> **Wybiral said:**
> Try:

```

int erg = system("sudo apt-get update");

```

Hi, Wybiral,
that's OK. But what about the hanging computer?
The call for APT running but not so good.
Bye Golly

---

### Post by Mr. C. on 2007-07-14
I don't believe your computer is hanging.  Perhaps you mean that this process is waiting for input.

Since we don't know what you've done in your program (like closing STDIN), we can't diagnose the problem.

You'll have to give more details than what you've given.

MrC

---

