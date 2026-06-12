---
title: "dash replacement for $BASH_SOURCE wanted"
date: 2013-03-07
forum: Programming Talk
---

### Post by mtadyshak on 2013-03-07
How would I port the bashism $BASH_SOURCE to dash? This gives the directory where the executable is located independent of the path from which the shell script was invoked. No #dash IRC channel on freenode.

---

### Post by schragge on 2013-03-07
Judging from the bash manpage, $BASH_SOURCE does something else. In a shell script outside of any functions $BASH_SOURCE should be identical to $0

But to get *what you're describing* in dash, I'd either
```

dirname `readlink -f $0`

```
or
```

abs_path=`readlink -f $0`
echo ${abs_path%/*}

```
or, if you're sure the script itself isn't symlinked
```

readlink -f ${0%/*}

```

---

