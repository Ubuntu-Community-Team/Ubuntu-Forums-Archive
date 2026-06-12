---
title: "Checking if the file descriptor is valid"
date: 2007-09-14
forum: Programming Talk
---

### Post by DBQ on 2007-09-14
Hey guys,
  Anybody knows how check whether a given file descriptor is valid?  I could not find anything reasonable online.  I am using C/C++.

Also, when a process forks off a child, does the child get its own 
STDIN_FILENO, and STDOUT_FILENO?

Thank you.

---

### Post by peabody on 2007-09-14
Don't know how to check if a number is a valid file descriptor.  However, as for stdin and stdout, the child will inherit the parents stdin and stdout.  You could use freopen to associate them to something else, however I think this will affect the parent process as well since children inherit file descriptors, but I could be wrong.

Simplest solution is to explicitly use some other stream.

---

### Post by dwhitney67 on 2007-09-15
A file descriptor that is anything other than -1 is considered valid.  I always forget which one is which, but stdin I believe has an "fd" of 0, stdout is 1, and stderr is 2.

Be careful with cout and cerr. These streams are _not_ thread-safe.  Thus if you have two threads, or a main process and a forked one sharing the same stream, your output could be intermingled.

---

