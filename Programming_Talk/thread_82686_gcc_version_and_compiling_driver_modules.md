---
title: "gcc version and compiling driver modules"
date: 2005-10-27
forum: Programming Talk
---

### Post by cwaldbieser on 2005-10-27
I was looking at an install script for an ethernet driver, and I noticed that it did a check to make sure that the version of gcc that is installed is the same as the version of gcc that was used to compile the kernel.  It checked /proc/version for this purpose.

On my (Breezy) system:
```

$ gcc -v 2>&1 | tail -1
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
$ cat /proc/version
Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:25:32 BST 2005

```
The gcc versions are different.  The install script seems to think this is a problem.  Is there some sort of compatibility mode I could use with my version of gcc to get around this?

Thanks!

---

### Post by toojays on 2005-10-27
You can install gcc-3.4, which is in the Ubuntu repository for this purpose.

---

