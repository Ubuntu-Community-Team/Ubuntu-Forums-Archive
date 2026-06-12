---
title: "semaphore / monitor / lock in C/C++ in ubuntu"
date: 2009-06-22
forum: Programming Talk
---

### Post by polarbear12345 on 2009-06-22
how can i protect a shared resource in C/C++ in ubuntu from simultaneous access...actually i have to maintain a log which will be accessable by a number of programs on network...

---

### Post by soltanis on 2009-06-22
You aren't very specific but I assume you are talking about multiple processes writing to the same log file, and you don't want them to corrupt it.

I also am not going to assume this file is on the local filesystem (you mentioned network, so I'll think NFS).

What you need are read/write locks.

[File locking with fcntl]("http://www.ecst.csuchico.edu/~beej/guide/ipc/flock.html")

Look at that URL; I found it really useful when I was writing programs that had to write to possibly the same files at once.

NFS (as well as all other POSIX-compliant file systems) supports locking via fcntl, if and only if the kernel hosting the filesystem supports kernel locks (which if you're running anything later than 2.4 you're good).

Basically, the page goes over it, but a read lock is where your program says, hey, I'm reading this file, so don't write to it. Multiple processes can read the same file at once. But if a process wants to modify the file, they need a write lock, where they essentially say that no one can read or write this file until the lock is released.

You'll usually want to lock the whole file, not just part of it.

Of course this is assuming you wrote these programs that will be writing to these logs yourself, so you can modify the source code (almost every language with C bindings supports locking somehow).

Also bear in mind that locks are advisory; if a program ignores file locks, it will do just that, fail to respect when another process has a lock on the file and will probably end up clobbering the file somehow.

So what you need to do is somehow get these processes to lock the log file before they attempt to write to it; which depending on how you are writing to this log (are you redirecting stdout? redirecting stderr? directing the programs to use a specific log) they may or may not do.

If you're piping output straight to these files, no locking will be done for you. You might want to consider piping output to an intermediate awk/perl program that locks the log files and pipes all their input into that file.

---

