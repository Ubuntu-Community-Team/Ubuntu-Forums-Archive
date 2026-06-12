---
title: "Java java.lang.Process"
date: 2008-07-07
forum: Programming Talk
---

### Post by rivera151 on 2008-07-07
Hi.  I'm kinda working on a program/API that can handle compiling from source automatically.  Since I'm using standard compiling tools, I need to run command line stuff.  While this is easily accomplished with the java.lang.Process, there is something that has given me trouble.  The javadoc says the following:

```
Because some native platforms only provide limited buffer size for standard input and output streams, failure to promptly write the input stream or read the output stream of the subprocess may cause the subprocess to block, and even deadlock.
```

I have run into this issue, where the buffer when it gets too big, the process hangs.  I have tried to find a way of finding out if the process is running to then grab the exit value, but the function that grabs the exit value throws an exception instead of returning some sentinel value.  And the API doesn't have an IsRunning() method or a Running or Exited field.

There are two questions here:
1.  How can I test if a process is still running so that I can keep checking if the buffer has been modified, and then read from it, to clear the text and avoid a buffer overrun leading to a crash?

2.  How can I avoid running into this buffer overflow?

That is all.  Thak you.

---

### Post by tinny on 2008-07-07
Posted twice???

[http://ubuntuforums.org/showthread.php?t=851741]("http://ubuntuforums.org/showthread.php?t=851741")

---

### Post by rivera151 on 2008-07-07
> **tinny said:**
> Posted twice???

[http://ubuntuforums.org/showthread.php?t=851741]("http://ubuntuforums.org/showthread.php?t=851741")

Yah, I think my browser skipped and I might've reposted.

If I don't find an admin, can somebody delete this copy thread?

---

