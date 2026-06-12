---
title: "IPC - msgget(), memget() API Documentation"
date: 2010-02-01
forum: Programming Talk
---

### Post by TennTux on 2010-02-01
I've been playing around with IPC lately in prep for a possible project. I found the headers in "sys/ipc.h", "sys/msg.h" and "sys/shm.h".

'man ipc' brings up SVIPC(7), this page references ipc(2), msgctl(2), msgget(2), msgrcv(2), msgsnd(2), ..., shmat(2), shmctl(2), shmdt(2), shmget(2), ftok(3)

However, when I try to bring up the referenced pages I get "No manual entry for XXXX". I found that the above headers where loaded with libc6-dev and the documentation was not included. I looked for a simularly named package and didn't find one for documentation. If a man page makes reference to another I'm going to assume (maybe my bad) that somewhere there is or was one.

**What Ubuntu Linux packages do I need to load to get doc for these commands?** HTML is prefered, man is good and I can deal with info or text based docs. I checked out glibc documentation just in case and found the following statements. "The GNU C library defines most of the facilities required by the SVID...", "The supported facilities from System V include the methods for inter-process communication and shared memory, ...", however, I didn't find any documentation for these commands.

As an aside I am aware of Pipes and looped back Sockets and I am considering them, however, this is as much about getting the complete picture as it is about the details.

---

### Post by dwhitney67 on 2010-02-01
In the ol' days, getting all of the manpages used to be easy.  Nowadays, I have noticed that Ubuntu decided to break the pages apart into separate packages.  I do not know the rationale for this; maybe it was to organize the pages into sub-categories, maybe it was to reduce the 'download-tax' on those with wimpy internet connections.

Anyhow, I believe the package you are interested is manpages-posix-dev.  You may also need others.
```

sudo apt-get install manpages-posix-dev manpages-dev

```

---

### Post by TennTux on 2010-02-01
Thanks that did it.

As you say, I don't know why they broke it up or why they named it that way then did. It would have helped if the documentation package was named similar to the library/header file package.

---

