---
title: "Memory allocation in Ubuntu"
date: 2010-09-17
forum: Packaging and Compiling Programs
---

### Post by shemp2718 on 2010-09-17
Wasn't sure where to post this.  I was just curious what type of protection there is to the OS when I compile and run a program that doesn't initialize pointer variables.  Is it possible to access memory allocated to the OS or any programs that are running?

---

### Post by BobvanderPoel on 2010-09-17
> **shemp2718 said:**
> Wasn't sure where to post this.  I was just curious what type of protection there is to the OS when I compile and run a program that doesn't initialize pointer variables.  Is it possible to access memory allocated to the OS or any programs that are running?

Short answer is NO.

Longer answer: you might be able to do that, but the OS makes it pretty hard to do. At the least you'd need to have your program run as root.

---

### Post by MadCow108 on 2010-09-17
yes you can access the memory of other processes e.g. with ptrace, if you have the privileges to do so (e.g. your own processes).
This is commonly used for debugging.

beginning with maverick even this will require root privileges.
You can probably also set this up for lucid and below somehow.

And you will generally not be able to mess with the kernels memory without root privileges (unless of course you use some kind of unpatched bug/exploit)

---

### Post by shemp2718 on 2010-09-17
Thanks BobvanderPoel and MadCow108 for the timely response!  I suspected that it would require a lot of work and of course I always follow my mothers advice, "Never run untested programs as root!"

---

