---
title: "Can I send stdout to a string?"
date: 2012-04-18
forum: Programming Talk
---

### Post by xytron on 2012-04-18
I'm working on a old program that sends all of it's output to stdout  and of course it prints on the screen, it's also simple to get the programs results to a file.

I'm wondering if it is possible to send the stdout data to a string, that is an array of char buffer, so that I don't have to use files but do everything in memory.


I tried using freopen() without success, because I could never actually view the contents of the buffer. I tried it like this;

```

freopen("NULL", "a", stdout);
setbuf(stdout, string_buf);




```


Thanks for any advice.

---

### Post by SeijiSensei on 2012-04-18
Try piping it to /run/shm/somefilename.  /run/shm is a virtual filesystem that Ubuntu creates by default using shared memory.  Will that help?

---

### Post by xytron on 2012-04-18
> **SeijiSensei said:**
> Try piping it to /run/shm/somefilename.  /run/shm is a virtual filesystem that Ubuntu creates by default using shared memory.  Will that help?

No, because I need a solution that will work on Unix and Windows, but thanks for the suggestion.

---

### Post by Tony Flury on 2012-04-19
can't you just write another program that reads data from stdin and processes it ?

Both Windows and Linux support piping - so you pipe stdout from the first process into stdin in your new program.

---

