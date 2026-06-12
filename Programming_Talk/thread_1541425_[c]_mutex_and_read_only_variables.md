---
title: "[c] mutex and read only variables"
date: 2010-07-29
forum: Programming Talk
---

### Post by dawwin on 2010-07-29
I've got following situation:
On program startup I set some variables in a structure. After that I run several threads and argument to thread function is const pointer to this structure. Structure is not modified while threads are running, but I can read this.
Do I have to use mutex in this case?

---

### Post by dwhitney67 on 2010-07-29
No, you do not require a mutex for read-only data.  You would want, but it is not 100% necessary, to use a mutex when dealing with simple data that is read/writable.  When dealing with complex data objects (ie. a linked list), then you would certainly use a mutex if the object is read/writable.

---

### Post by dawwin on 2010-07-29
Thanks

---

