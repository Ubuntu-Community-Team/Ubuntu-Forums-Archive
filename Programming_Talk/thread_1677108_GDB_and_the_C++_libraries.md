---
title: "GDB and the C++ libraries"
date: 2011-01-28
forum: Programming Talk
---

### Post by hgernhardt on 2011-01-28
So I was to figure out why cin won't block after dumping the input buffer when piping data into the program.  As it turned out, I discovered the easiest thing to do was to make piped input an error condition for the program and bail out.  Yes, this was a homework assignment.

Anyway, in trying to wrap my brain around the problem, I began by invoking GDB.  My compile line was:
```

g++ -g -D_GLIBCXX_DEBUG src/homework.cpp -o bin/homework

```
So now I want to look at the status of the input stream in GDB.  Unfortunately, when I invoke gdb and set a breakpoint:
```

(gdb) print cin
$2 = <incomplete type>
(gdb) print cin.rdbuf()->in_avail()
Couldn't find method std::istream::rdbuf
(gdb)

```
I've installed the debug libraries for stdc++.  What am I missing here?

Thanks,

Henry

---

