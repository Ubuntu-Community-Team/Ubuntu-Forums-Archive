---
title: "If memory under &quot;free -m&quot; is cached, it should be automatically freed, right?"
date: 2010-07-13
forum: Programming Talk
---

### Post by Zorgoth on 2010-07-13
Because I think I may have encountered a matlab bug; my script gave an "OUT OF MEMORY" error when there was 1.2 GB of memory listed as "cached" under free -m (I was having it update every 5 seconds), and that memory was still cached after the error.  Is this a bug in matlab's out of memory error or does that memory count as in use?

---

### Post by Zorgoth on 2010-07-13
I was running matlab using matlab-emacs in emacs in tty1, not in my X session.

---

### Post by trent.josephsen on 2010-07-13
Virtual machines such as the JVM for Java often have their own limits on memory usage, not related to the memory size of the system.  Among other reasons, this prevents a Java program from stealing memory from essential system processes.  I'm not familiar with Matlab internals, but I'm guessing it's the same issue.  You might, by searching, find a way to increase the amount of memory available to Matlab.

---

### Post by Zorgoth on 2010-07-13
I think the problem is that 32-bit matlab is for whatever reason restricted to ~3GB of memory even though my system has access to more.  I will probably try installing 64-bit matlab.  Putting 64-bit linux on would require way too much recustomization.

---

### Post by Zorgoth on 2010-07-13
that didn't make any sense, i can't install that.  idiot.  I'll just run it on the server.

(Note I mean myself not anyone else)

---

