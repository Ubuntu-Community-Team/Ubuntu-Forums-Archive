---
title: "forgot to delete shared memory file in main program"
date: 2007-10-07
forum: Programming Talk
---

### Post by EzarKun on 2007-10-07
Hi,
newbie here.

I made a program first, without using 
shmdt
but later put it in
i was wondering how to clean the place the shared memory is placed cause, whenever I run the program, it gives an error that the shared memory already exists.

thanks

---

### Post by dwhitney67 on 2007-10-07
It's been years (14 to be exact) since I've worked with shared memory between programs.  I believe the process that created the shared memory needs to call shmctl() when it is done with the segment, but I could be wrong.

In code, the usage is:
```

#include <sys/ipc.h>
#include <sys/shm.h>

...

shmctl( shmid, IPC_RMID, 0 );
```

---

