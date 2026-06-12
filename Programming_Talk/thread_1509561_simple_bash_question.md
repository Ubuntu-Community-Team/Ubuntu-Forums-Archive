---
title: "simple bash question"
date: 2010-06-14
forum: Programming Talk
---

### Post by glederfein on 2010-06-14
I want to write a bash script that makes a directory in a path with spaces in it.
For example:

```

#!/bin/bash
dir="/cygdrive/c/Documents and Settings/guy/My Documents"
mkdir $dir/new

```

For some reason this splits up the $dir variable (by spaces) and mkdir fails.

Please help.

---

### Post by Bachstelze on 2010-06-14
You must wrap it in quotes. Also, there's no reason to use /bin/bash for something that simple, just use /bin/sh:

```
#!/bin/sh
dir="/cygdrive/c/Documents and Settings/guy/My Documents"
mkdir "$dir/new"
```

---

### Post by MadCow108 on 2010-06-14
also mkdir fails when the parent does not exist.
solution: add -p flag so it creates the parent too.

---

