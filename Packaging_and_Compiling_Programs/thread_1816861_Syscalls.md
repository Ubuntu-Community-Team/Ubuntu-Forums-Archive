---
title: "Syscalls"
date: 2011-08-02
forum: Packaging and Compiling Programs
---

### Post by piscoster on 2011-08-02
Hey guys,

i guess so this is the right section...

Ok i am coding asm a little and want to find out where the syscalls for ubuntu version 10.04 are...

Does anybody know the path?

greetings

---

### Post by Bachstelze on 2011-08-02
The path to what?

---

### Post by piscoster on 2011-08-02
to the file where I can find the syscalls...

Do you know what I am looking for?

thx in advance:KS

---

### Post by SevenMachines on 2011-08-02
If you install manpages-dev then you should have 
$ man syscalls

libc6-dev has /usr/include/unistd.h which *might* be what you're looking for

---

### Post by Bachstelze on 2011-08-02
No, I don't. What do you mean by "the syscalls"? If you mean the code that implements them it's in the kernel source

[http://www.linuxforums.org/forum/kernel/6871-where-do-i-find-system-call-implementation-code.html](http://www.linuxforums.org/forum/kernel/6871-where-do-i-find-system-call-implementation-code.html)

---

### Post by piscoster on 2011-08-02
thx for your answer:D

greetings

---

