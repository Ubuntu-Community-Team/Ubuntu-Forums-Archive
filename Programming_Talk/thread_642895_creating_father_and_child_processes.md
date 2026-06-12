---
title: "creating father and child processes"
date: 2007-12-17
forum: Programming Talk
---

### Post by tashe on 2007-12-17
How do i create in C, one father process and 2 child processes and then sleeps for n seconds, and wakes up?
Thanks

---

### Post by geirha on 2007-12-17
You use [fork]("http://en.wikipedia.org/wiki/Fork_%28operating_system%29")()

---

### Post by tashe on 2007-12-17
I know the fork command but I am confused with the PID and that stuff? Can you be more precise? drop a few lines of code plz  :)

---

### Post by geirha on 2007-12-17
There's an example at the link I posted. [http://en.wikipedia.org/wiki/Fork_%28operating_system%29](http://en.wikipedia.org/wiki/Fork_%28operating_system%29)

---

### Post by uljanow on 2007-12-17
Creating father processes doesn't make sense.
```

pid_t pid
if ((pid = fork()) < 0) {
   perror("fork");
   exit(1);
} else if (pid)
      // father
else
   // child		

```

---

### Post by moma on 2007-12-17
Hello,

This [Beej's...]("http://beej.us/guide/") guide is good:
[http://beej.us/guide/bgipc/output/html/singlepage/bgipc.html#fork](http://beej.us/guide/bgipc/output/html/singlepage/bgipc.html#fork)

Other important C/C++ manuals for Linux:
[http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)

Merry xmas,
$ sudo apt-get install xsnow
$ xsnow  # on your desktop

---

