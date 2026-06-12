---
title: "quick question: using ulimit to control stack size"
date: 2006-01-07
forum: Programming Talk
---

### Post by veraction on 2006-01-07
I had a C program using a lot of resources & it would get stack overflows. I wanted to increase stack. eventually I found the way to by using 

To show stack size:
```
$ulimit -s
```
To change stack size:
```
$ulimit -s *bytes*
```

**but why is it that once I start a new terminal, I can only change the stack change once?**

```

$ ulimit -s
8192
$ ulimit -s 6000
$ ulimit -s
6000
$ ulimit -s 6005
bash: ulimit: stack size: cannot modify limit: Operation not permitted

```

(note, it seems like each terminal has its own settings for ulimit... if I set it in one, it doesn't affect the other terminal, etc)

---

### Post by coredump on 2006-01-07
Yes, it's a per-process limit, so one terminal session won't affect another.

But why it's failing on the second try, I don't know.  Does the 'man' page say anything about it?  Or the 'man' page for the underlying system call?

---

### Post by cylon359 on 2006-01-07
You should try fix your program to use less stack, and start allocating via malloc

---

### Post by veraction on 2006-01-07
Its a GMP issue: [http://www.swox.com/gmp/#FAQ](http://www.swox.com/gmp/#FAQ) Q3

Guess malloc would work, as that GMP link says, but makes it slower (and due to nature of the problem I'm working on, I want it to go fast & and utilize more than 8MB -- default).

Anyways, I don't seem to have a man page entry for ulimit on my machine.I found a link here: [http://www.ss64.com/bash/ulimit.html](http://www.ss64.com/bash/ulimit.html) but doesn't say why I can't change it twice in same terminal.

Not really an issue. Was just wondering

---

### Post by LordHunter317 on 2006-01-07
[edit]Need to lookup correct information

---

### Post by cylon359 on 2006-01-08
Well, in that case, try running ulimit through sudo...

---

### Post by veraction on 2006-01-08
Ah, well, I guess I can keep lowering it, but can only raise it once:

```

$ ulimit -s
8192
$ ulimit -s 5000
$ ulimit -s
5000
$ ulimit -s 4000
$ ulimit -s
4000
$ ulimit -s 6000
bash: ulimit: stack size: cannot modify limit: Operation not permitted
$ sudo ulimit -s 6000
Password:
sudo: ulimit: command not found

```

---

### Post by coredump on 2006-01-08
OK, the man page for 'ulimit' is part of 'bash', so do 'man bash' and then search (using '/') for 'ulimit'.  Not that it helps much!

The underlying system call is no longer called 'ulimit' but is now 'setrlimit'.  But that man page is missing from Ubuntu (at least on my Mac/PowerPC install of 5.04).  So, on another Linux box (Slackware 10.1), I got these excerpts:

```
The  soft  limit is the value that the kernel enforces for
the corresponding resource.  The  hard  limit  acts  as  a
ceiling  for  the  soft limit: an unprivileged process may
only set its soft limit to a value in the range from 0  up
to  the  hard  limit,  and  (irreversibly)  lower its hard
limit.  A privileged process may make arbitrary changes to
either limit value.
```

```
RLIMIT_STACK
       The  maximum  size  of the process stack, in bytes.
        Upon reaching this limit, a SIGSEGV signal is  gen*
        erated.   To  handle  this  signal,  a process must
        employ an alternate signal stack  (sigaltstack(2)).
```

```
The above struct was taken from BSD  4.3  Reno.   Not  all
fields  are meaningful under Linux.  Right now (Linux 2.4)
only the fields ru_utime, ru_stime, ru_minflt,  ru_majflt,
and ru_nswap are maintained.
```

So, I think you'll need to check the man page for 'setrlimit' on a machine with a 2.6 kernel, to see if that last paragraph still applies.

I also did dome more testing with 'ulimit' from the command line, and it seems you can use 'ulimit' a second time, but only to reduce your stack size -- not increase it!  So I think that the first paragraph above has something to do with this, where it mentions 'privileged processes'.  This means processes owned by 'root', of course, which can set their limits any way they want.  Whereas ordinary user processes cannot, and it appears that they can only reduce limits, not increase them.

Hope this all makes sense!

---

### Post by cylon359 on 2006-01-08
Try to use setrlimit in your code (man setrlimit)?

However, you'll have to setuid your binary to after giving it root ownership...

---

