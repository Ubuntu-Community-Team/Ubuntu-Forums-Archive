---
title: "directory manipulation"
date: 2007-11-26
forum: Programming Talk
---

### Post by corefile on 2007-11-26
I have a directory, lets day /dir1 and in /dir1 I have several other directories, and in those directories I have several files, and I want to delete all the files ending in .deleteme in all the directories under /dir1
 is this possible with the "rm" command?

---

### Post by ThinkBuntu on 2007-11-26
Here's how I'd do it with my basic Bash shell knowledge:

```
$ rm dir1/*.deleteme
$ rm dir1/*/*.deleteme

```

And so on. Use more */ for each level of directories.

---

### Post by volanin on 2007-11-26
**$ find /dir1 -name '*.deleteme' -exec rm {} \;**

---

### Post by corefile on 2007-11-26
> **volanin said:**
> **$ find /dir1 -name '*.deleteme' -exec rm {} \;**

If I do that from the command line this is what I get

find: missing argument to `-exec'

*edit* wait I found the problem, I didn't have a space after {}

---

### Post by volanin on 2007-11-27
> **corefile said:**
> If I do that from the command line this is what I get
find: missing argument to `-exec'

You probably mistyped it.
I tested it here, and it is ok.
Please copy and paste, and test again!
:)

---

### Post by corefile on 2007-11-27
worked! Thanks for the quick response

---

