---
title: "Using &quot;chmod&quot; in a simple shell script"
date: 2011-06-03
forum: Programming Talk
---

### Post by Matodo on 2011-06-03
Hello

I'm trying to write a shell script that takes a folder name as an argument, and deletes "x" permissions for all files inside thas folder and in each subfolder.

Here is what I tried:
> #!/bin/bash
fname=$1
chmod -x -R $fname

The problem is, I can't access those folders after executing that script. I only hoped to apply those changes on ordinary files inside those folders, but not on folders themselves.

How can I do it?
Thanks a lot :)

---

### Post by cgroza on 2011-06-03
I suggest you recursively cd to each folder to apply your chomd command.

---

### Post by matt_symes on 2011-06-03
Hi

```
#!/bin/bash

# Use find.
find "$1" -maxdepth 0 -type f -exec chmod -x '{}' \;
```Quote your paths or paths with spaces may give you problems.

-maxdepth 0 option will only change in that directory. Adjust -maxdepth for other depth traversals in the file system or remove -maxdepth to recurse to bottom of tree from the path passed.

Add error  checking for the path as well. Make sure it exists ;)

Kind regards

---

### Post by Petrolea on 2011-06-04
> **Matodo said:**
> Hello

I'm trying to write a shell script that takes a folder name as an argument, and deletes "x" permissions for all files inside thas folder and in each subfolder.

Here is what I tried:


The problem is, I can't access those folders after executing that script. I only hoped to apply those changes on ordinary files inside those folders, but not on folders themselves.

How can I do it?
Thanks a lot :)

How about adding 'read' at the same time?

---

