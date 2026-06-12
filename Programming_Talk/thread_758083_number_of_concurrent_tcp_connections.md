---
title: "number of concurrent tcp connections"
date: 2008-04-17
forum: Programming Talk
---

### Post by Googler on 2008-04-17
i'm building a c++ TCP server under ubuntu
the problem is that it can't serve more than 1023 concurrent connection
so is there a way to make this number much more bigger?

thanks in advance

---

### Post by stroyan on 2008-04-18
You are probably making all of the tcp connections from one process and hitting the default limit on number of open files per process.
You can confirm that limit with 'ulimit -a' or 'ulimit -n' at a shell prompt.
You could increase that limit with 'ulimit -n <number>' or setrlimit() as root or by editing /etc/security/limits.conf .

---

### Post by Googler on 2008-04-20
> **stroyan said:**
> 
You could increase that limit with 'ulimit -n <number>' or setrlimit() as root or by editing /etc/security/limits.conf .

after editing limits.conf the tcp server hangs up and refuse to accept more than 1023 connections

any other solutions

---

### Post by stroyan on 2008-04-20
You could use the strace command to record the parameters and results of system calls made by your program.
That would give more information about what resource limit the program was reaching.

---

