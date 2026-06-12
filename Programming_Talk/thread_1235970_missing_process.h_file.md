---
title: "missing process.h file"
date: 2009-08-09
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-08-09
I'm missing the process.h header file; is there any place I can download the file from?  Or if anybody has it can you attach the file in your post so I can download it?

Any other suggestions/solutions would be appreciated.

Thanks

---

### Post by wojox on 2009-08-09
```
/* 
 * Copyright (C) 2000 - 2008 Jeff Dike (jdike@{addtoit,linux.intel}.com)
 * Licensed under the GPL
 */

#ifndef __PROCESS_H__
#define __PROCESS_H__

#include <signal.h>

/* Copied from linux/compiler-gcc.h since we can't include it directly */
#define barrier() __asm__ __volatile__("": : :"memory")

extern void sig_handler(int sig, struct sigcontext *sc);
extern void alarm_handler(int sig, struct sigcontext *sc);

#endif
```

---

### Post by c0mput3r_n3rD on 2009-08-09
That file doesn't include the function such as _beginthread and _endthread though.  Does it help to know that it's for c++?

---

### Post by wojox on 2009-08-09
Sorry just C

---

### Post by c0mput3r_n3rD on 2009-08-09
> **wojox said:**
> Sorry just C

Alright thanks anyway.

Can any one else help?

---

### Post by Can+~ on 2009-08-09
Not a big fan of Boost (or C++ for that matter), but check:

[http://www.boost.org/doc/libs/1_39_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_39_0/doc/html/thread.html)

---

### Post by wojox on 2009-08-09
[http://doc.ddart.net/msdn/header/include/process.h.html](http://doc.ddart.net/msdn/header/include/process.h.html)

---

### Post by c0mput3r_n3rD on 2009-08-09
Thanks for the file, unfortunately it's only for Windows or Mac :(

Is there a package I can install that includes process.h?

The link you (can+~) sent me does not seem to give you a link to download the file, but instead just describes the libraries and their functions.  Am I missing something?

I appreciate all your help.

---

### Post by Can+~ on 2009-08-09
> **c0mput3r_n3rD said:**
> The link you (can+~) sent me does not seem to give you a link to download the file, but instead just describes the libraries and their functions.  Am I missing something?

I appreciate all your help.

It's part of the whole library called boost, it's available on the repository, usually under "libboost"

---

### Post by c0mput3r_n3rD on 2009-08-09
> **Can+~ said:**
> It's part of the whole library called boost, it's available on the repository, usually under "libboost"

Ok I found it in Synaptic Package Manager and I'll check it out.  Thank you.

---

