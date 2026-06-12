---
title: "Running something on shutdown from rc0"
date: 2007-09-16
forum: Programming Talk
---

### Post by musther on 2007-09-16
I developed and maintain a small script - AutoFsck - which automates fsck in an interactive manner.  It makes it possible to run fsck when you logout, rather than on boot.

The biggest problem with it in its current state is that it restarts the machine, runs fsck, and then shuts the machine down - ideally it would run fsck on shutdown.

So, I'm playing around with ways to do that, first I created /etc/rc0.d/S89autofsck - I used S89 because it was after unmount root and before S90halt.

The file contained:

```
#!/bin/bash
#
echo -ne \\a
fsck -A
exit
```

This was to be the initial test, and indeed, the machine beeped at the echo command, and then shut down, fsck -A didn't seem to do anything, I've also tried 'fsck' and 'fsck /dev/sda2' with no luck.

Anyone know why it's not working?

Cheers

---

### Post by tgalati4 on 2007-09-17
I would guess that echo is part of bash so it gets executed immediately.

fsck would require that a thread be created to run it.  Once shutdown has commenced, threads are being terminated.  I would guess that shutdown also puts the kernel into a state of not accepting new threads.

A kernel hacker can provide a better answer.

---

### Post by musther on 2007-09-17
I was afraid it might turn out to be something like that, but it's hard to find a concrete answer - and to possibly find a way around it.

---

