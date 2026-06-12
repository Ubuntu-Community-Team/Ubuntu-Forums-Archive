---
title: "Maximum array size in Ubuntu (Kernel)"
date: 2013-05-13
forum: Programming Talk
---

### Post by mikeduk on 2013-05-13
I've been messing around with NetFilters today and have run into quite a lot of system crashes that I can't put my finger on but it feels like a memory-being-stepped-on issue.

Strangely they now seem to have gone away and I don't know its just that the memory issues has moved as they often do or if a change has fixed it.. therefore highlighting the problem!

Here is the original code:

```

#define N_BUCKETS 100000


struct hash_conn_state {
    int packetsRecv;
    int packetsSent
};


struct hash_conn_state* conn_state[N_BUCKETS];

```

The problems appear to be related to accessing that array. I've now changed it to this...

```

#define N_BUCKETS 10000


struct hash_conn_state {
    int packetsRecv;
    int packetsSent
};


struct hash_conn_state* conn_state[N_BUCKETS];



```

As you can see the only difference is the size of the array.. it has changed from 100,000 to 10,000... I appreciate that this really should have been done as a dynamic array in first place using kmalloc but could that really explain my problem? Is there some sort of limit on the fixed array size?

---

### Post by TheFu on 2013-05-13
Of course there is a limit. 
If you run bash, run **ulimit -s** to see the stack size limit.  **man bash** explains more.
You can modify the limit.  Understanding the stack and the heap is a good thing for programmers.

---

### Post by dwhitney67 on 2013-05-13
Allocate the memory your app (or kernel driver) require; avoid declaring such a large buffer on the stack.  My $0.02.

---

### Post by mikeduk on 2013-05-14
Yes I've changed the code now to allocate the array of * on init instead.

But I'm curious about the stack limit.. running ulimit -s returns an 8k limit.. how does that work for modules, is that 8k for all modules combined or would each module get that 8k?

---

