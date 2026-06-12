---
title: "[C++] Events: pthreads or semaphores"
date: 2009-07-15
forum: Programming Talk
---

### Post by wbest on 2009-07-15
I'm trying to convert some windows code in C++ to Linux.
Its not my code, just so you know.

Anyway, I'm trying to decide what is the best thing to replace "Events" with.
The code uses CloseHandle(pv_hEvent), SetEvent(pv_hEvent), CreateEvent(NULL, bManualReset, false, NULL) etc

Here pv_hEvent is of type "HANDLE." And all of these are wrapped up in a class called XEvent.  The wait method is infinite, and there is a ResetEvent method, but I intend to skip it as Linux has auto reset only.

Now, my first thought was to use POSIX semaphores, with semaphore.h, but I'm not sure that's correct.  I'm also tempted to use pthreads from pthread.h

I've been trying to follow these directions: [http://www.ibm.com/developerworks/library/l-ipc2lin2.html](http://www.ibm.com/developerworks/library/l-ipc2lin2.html)

but I'm not getting all the info i need from it.

---

### Post by dwhitney67 on 2009-07-15
I just worked on a VC++ project that used the CreateEvent().  The application relied on serial port communications to receive/send data.

I augmented the application to use a UDP socket.  I had no need for the "handles" offered by CreateEvent().

To determine if there is any activity on the UDP socket, I used a select().  If I had developed the code for *nix, I would've done the same.

Therefore, try to figure out why your application uses CreateEvent(), then determine how that maps over to the *nix world, if at all.

---

