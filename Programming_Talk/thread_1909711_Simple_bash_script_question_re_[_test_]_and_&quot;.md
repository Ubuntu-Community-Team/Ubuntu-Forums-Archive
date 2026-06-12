---
title: "Simple bash script question re: [ test ] and &quot;$quotes&quot;"
date: 2012-01-15
forum: Programming Talk
---

### Post by Stovey on 2012-01-15
Hi everyone!  Would someone please explain the difference between the following 3 while statements.  #1 & #2 work but #3 does not.  How is bash interpreting these statements?  

1. while [ -n "$paths" ]; do
2. while [ $paths ]; do
3. while [ -n $paths ]; do

```
paths=$PATH:
dir=""

while [ -n "$paths" ]; do
    dir=${paths%%:*}
    echo $dir
    paths=${paths#*:}
done
```

---

### Post by Arndt on 2012-01-16
> **Stovey said:**
> Hi everyone!  Would someone please explain the difference between the following 3 while statements.  #1 & #2 work but #3 does not.  How is bash interpreting these statements?  

1. while [ -n "$paths" ]; do
2. while [ $paths ]; do
3. while [ -n $paths ]; do

```
paths=$PATH:
dir=""

while [ -n "$paths" ]; do
    dir=${paths%%:*}
    echo $dir
    paths=${paths#*:}
done
```

The meaning of the [ ] test is given by the 'test' program (see "man test"). In the third form, when $paths is empty, it becomes

```
[ -n ]

```
which is not valid since -n needs an argument.

---

### Post by sisco311 on 2012-01-16
Bash has a test buildin command which supersedes test(1) (/usr/bin/test). [ is a synonym for test (but requires a final argument of ]). See:
```
help [
help test
man bash | less +/"^CONDITIONAL EXPRESSIONS"

```
and BashFAQ 031 (link in my signature).

---

### Post by Arndt on 2012-01-16
> **sisco311 said:**
> Bash has a test buildin command which supersedes test(1) (/usr/bin/test). [ is a synonym for test (but requires a final argument of ]). See:
```
help [
help test
man bash | less +/"^CONDITIONAL EXPRESSIONS"

```
and BashFAQ 031 (link in my signature).

Does this change the answer?

---

### Post by sisco311 on 2012-01-16
> **Arndt said:**
> Does this change the answer?

Nope, just wanted to point out that Bash has its own version of `test' which is not the same as the `test' command from GNU/coreutils or the `test' utility specified by POSIX.

---

