---
title: "Eclipse: watch vectors"
date: 2009-05-10
forum: Programming Talk
---

### Post by Losik on 2009-05-10
I've downloaded "Eclipse IDE for C/C++ Developers". It's really great but there is a problem. Since I'm a beginner in programming watch list is very important for me. But while debugging I cannot watch vectors. I mean I want to see their elements but can only see something like on the picture ('pos' is a vector <int>). So is there any easy way to watch vectors in this IDE? 

[[IMG]http://i074.radikal.ru/0905/89/f37f7a4ef8f2t.jpg[/IMG]](http://radikal.ru/F/i074.radikal.ru/0905/89/f37f7a4ef8f2.jpg.html)

---

### Post by dwhitney67 on 2009-05-10
I believe you need to examine the value(s) that are pointed to by _M_start.

I know how to manually examine individual values using gdb, which is what Eclipse uses, but I have no idea how to set up a watch-list within Eclipse.

After all, _M_start only points to the first element of the internal allocated memory within the vector.  I believe this memory is contiguous, so indexing into _M_start is achievable.

For instance, in gdb:
```

gdb> print *(myvec._M_impl._M_start+2)

```
will print the third value in the vector.  Note, gdb has to know how to print the value; if it is an int, then no sweat.  Printing a more complex object may not be doable.

---

