---
title: "Loop through a directory, output the names of directories With BASH"
date: 2009-06-15
forum: Programming Talk
---

### Post by condonm on 2009-06-15
Hi,
So I'm having a little bit of trouble figuring this out. If you can help that would be awesome.
Basically I need a BASH script that creates a loop that goes through the contents of a directory and outputs the names of the directories.

Any help is greatly appreciated.

---

### Post by shel-hall on 2009-06-15
> **condonm said:**
> Hi,
So I'm having a little bit of trouble figuring this out. If you can help that would be awesome.
Basically I need a BASH script that creates a loop that goes through the contents of a directory and outputs the names of the directories.
Do you have to have a loop, say for some silly CS class assignment, or would a simple command do?

```

find somedirectory -type d

```

... ought to do the trick.

-Shel

---

