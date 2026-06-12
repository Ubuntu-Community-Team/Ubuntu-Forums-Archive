---
title: "[SOLVED] Bash: not able to redirect the output via pipes"
date: 2007-09-25
forum: Programming Talk
---

### Post by Ces on 2007-09-25
[COLOR="DarkGreen"]***Edit. My bad, the last example in this post actually do work. It seems I simplified my test case so much that the problem went away. Now then, I have made a new test case in post number four. Please scroll down.***[/COLOR]


**What I have**
Let us say that I have counted the number of lines of the file *foo* which contains the pattern *bar*. (Let us assume that **grep** finds 42 lines.) I am using **bash**.

```
$ grep -c bar foo
42
```


**What I want to do**
Take the number of lines (42) and check if it is less than for instance 108. Like this.
```
$ test 42 -lt 108
```
How can I make this work when I do not manually enter the number of lines? Or, differently said, how can I substitute the value *42* above with the standard output of **grep**?


**What I cannot get to work**
A few examples of what I have tried, so you may understand my way of reasoning. I guess I fail at understanding the very basics of redirecting and in/outputs.

Redirecting the output of **grep** into **test**... (Error: Unary operator expected.)
```
$ grep -c bar foo | test -lt 108
```

Using the command&#8217;s value as argument... (I&#8217;m assuming it is using the exit code rather than the standard output.)
```
$ test `grep -c bar foo` -lt 108
$ echo $?
0
```

---

### Post by Jussi Kukkonen on 2007-09-25
last one works, doesn't it?

---

### Post by ghostdog74 on 2007-09-25
> **Ces said:**
> [B]
```
$ test `grep -c bar foo` -lt 108
$ echo $?
0
```
this is correct. try changing -lt to -gt , and see what $? is. it should be 1. So you can test for 0 or 1.

---

### Post by Ces on 2007-09-25
Hmm... The last example does indeed work. It seems my problem is another, let me expand the search pattern somewhat.

**The file *foo***
[INDENT]bar bar
bar foo
foo bar
foo foo
[/INDENT]


**Works**
Grep’ing and test’ing the pattern *bar* anywhere on each line.
```
$ test `grep -c bar foo` -eq 3 ; echo $?
0
```


**And now the file *foo2***
[INDENT]\bar bar
\bar foo
\foo bar
\foo foo
[/INDENT]


**Works not**
Grep’ing and test’ing the pattern *\bar* anywhere on each line.
```
$ test `grep -c '\\bar' foo2` -eq 2 ; echo $?
1
```
(While **grep -c '\\bar' foo2** returns the value **2**.)


**Concluding question**
Why can I not redirect the output when using backslashes in the search pattern?

---

### Post by ghostdog74 on 2007-09-25
try this:
```

grep -c  "[\]bar" file

```

---

### Post by Ces on 2007-09-25
Thanks. Works like a charm. :)

---

