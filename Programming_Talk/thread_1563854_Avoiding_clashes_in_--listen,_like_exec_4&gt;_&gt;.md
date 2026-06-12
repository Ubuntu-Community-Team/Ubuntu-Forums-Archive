---
title: "Avoiding clashes in --listen, like exec 4&gt; &gt;(fn)"
date: 2010-08-29
forum: Programming Talk
---

### Post by davidpbrown on 2010-08-29
If I run a simple bash script notification, for example

```
exec 4> >(zenity --notification --listen)
```

how can I be sure there won't be a clash between two scripts on the same channel?

Obviously, I could number each script uniquely but then I've got to keep a tab on that number.

So exec 3> or exec 4> etc.

Is there an option to assign the number of the next available channel to a local variable for that script?

---

### Post by geirha on 2010-08-30
There's no clash; every process have their own set of fds, they are inherited by child processes however.

E.g.
```

$ exec 4> >(rev)
$ bash -c 'echo foo >&4'
oof
$ exec 4>&-

```

```
$ bash -c 'exec 4> >(rev); read' &
[1] 16306
$ echo foo >&4
bash: 4: Bad file descriptor

```
In the latter, fd 4 is opened by a child process, and you can see it does not affect the parent.

---

