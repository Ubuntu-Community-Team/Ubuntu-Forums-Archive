---
title: "simplle os calls in c++, better to wrap up a bash command or find a c++ way?"
date: 2010-04-13
forum: Programming Talk
---

### Post by Søren on 2010-04-13
this is just something im curious about because i dont want to teach myself bad habits. if i need to do a simple file processing command like say make a directory, should i just put a bash expression inside a system () thingy like:

```
system( " mkdir mydir ");

```of should i do it in c++ with a function or something?

---

### Post by phrostbyte on 2010-04-13
It's better to use the native syscalls, I would say. The mkdir command is just a friendly wrapper around the mkdir() syscall.

eg: 

#include <sys/stat.h> 
mkdir("/path/to/dir", S_IRUSR);

---

### Post by Søren on 2010-04-13
sweet cheers.

---

