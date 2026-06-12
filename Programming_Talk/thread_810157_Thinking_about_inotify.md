---
title: "Thinking about inotify"
date: 2008-05-28
forum: Programming Talk
---

### Post by tinkertim on 2008-05-28
I've been planning a backup solution based on a few kinds of versioning/copy on write file systems such as ext3cow. The idea is to intelligently back up things in a gradient fashion from any kind of fs to a copy on write storage server. 

For instance, if foo.txt is modified xx times, it gets backed up to a CoW file system and a snapshot is taken. A simple glob syntax configuration will set the frequency / gradient and retention.

The easiest route to this is going to be inotify, however I'm really concerned about the fact that the kernel will store full path names per file. It will be very easy to store modification events in a sqlite database, which means a list of files to back up is just a query away. I'm hoping inotify will work for me.

The default # of watches is 8192, so the bloat in the default case has to be envisioned at 8192 * POSIX_PATH_MAX (255). On busy web servers, one would quickly run out of watches and need to raise that limit.

I'm wondering, is anyone using inotify to watch beyond 8k files, if so how much of a performance hit did you notice?

Thanks to any who care to share their experiences.

---

### Post by 23meg on 2008-05-28
Moved to Programming Talk.

---

