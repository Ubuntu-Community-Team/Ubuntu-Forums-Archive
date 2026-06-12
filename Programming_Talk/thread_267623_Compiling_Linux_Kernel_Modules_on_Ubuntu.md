---
title: "Compiling Linux Kernel Modules on Ubuntu"
date: 2006-09-28
forum: Programming Talk
---

### Post by boecke on 2006-09-28
Does anyone else have the same problem when they attempt to compile Kernel Modules on Ubuntu? I've done everything and i always manage to get this compiler error. There is nothing wrong with the code as it is as basic as I could make it ("Hello World").

```

In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from main.c:4:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from main.c:4:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from main.c:4:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
main.c:14: error: conflicting types for ‘cleanup_module’
/usr/include/linux/module.h:55: error: previous declaration of ‘cleanup_module’ was here

```

Any pointers? (aha.. :rolleyes:)
Cheers.

---

