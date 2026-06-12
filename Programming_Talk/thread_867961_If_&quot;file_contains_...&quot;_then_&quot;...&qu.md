---
title: "If &quot;file contains ...&quot; then &quot;...&quot; else &quot;...&quot; fi"
date: 2008-07-23
forum: Programming Talk
---

### Post by antm88 on 2008-07-23
I am very lost here, its something I would have expected to be easy to do! Or at least find out how to do :|

So say I want to search a specific file for STRING and execute a bash command if it exists in the file. What is the command for this?

Thanks, Ant

---

### Post by WW on 2008-07-23
Here's one way:
```

grep STRING file -q && echo 'Found it!'

```
E.g.
```

$ grep "main" main.cpp -q  && echo 'Found it!'
Found it!
$ grep "xxxyyyzzz" main.cpp -q  && echo 'Found it!'
$

```
Replace the echo command with the command to be run if the string is found.

---

### Post by antm88 on 2008-07-23
Thanks, that's perfect!

---

