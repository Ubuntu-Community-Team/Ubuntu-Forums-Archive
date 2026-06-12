---
title: "BASH - setting variables"
date: 2012-05-24
forum: Programming Talk
---

### Post by layr on 2012-05-24
Let's say there's a cron job
```
00 19 29 05 * /home/laur/Documents/comp/scripts/todo.sh "some random text quoted" May 29 19:00

```in other words it'll run todo.sh with 4 arguments.

If $1 was echoed in todo.sh, it would print **some random text quoted**.

Then again, if I ran 
```
set $(cat $cron | sed -n 1p | cut -c20-)
```($cron being file containing cron jobs in a format shown above)

, then $2 would return as **"some** instead of **some random text quoted**.

Why is that so?

---

### Post by Vaphell on 2012-05-25
in first case quotes are outside the string, interpreted by the shell
in second "" become the part of the string and they show up in output while not preventing breaking on spaces

2nd case is equivalent to
```
x='abc "some random text quoted"'
echo "$x"
set $( echo "$x" )
echo $1
echo $2
```
```
abc "some random text quoted"
abc
"some
```

here "" are interpreted, words are treated as a single string
```
set abc "some random text quoted"
echo $1
echo $2
```
```
abc
some random text quoted
```
that level of indirection in case #2 changes everything


if you need to do *set $()* you can use eval though eval should be avoided as it allows execution of any string which may have dire consequences
```
x='abc "some random text quoted"'
echo "$x"
eval "set $x"
echo $1
echo $2
```
```
abc "some random text quoted"
abc
some random text quoted

```

---

### Post by layr on 2012-05-25
Thanks, got it working!
But as I understand, eval seems to be the only way the wanted result can be achieved?

---

