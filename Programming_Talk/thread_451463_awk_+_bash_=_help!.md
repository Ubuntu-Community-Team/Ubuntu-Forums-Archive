---
title: "awk + bash = help!"
date: 2007-05-22
forum: Programming Talk
---

### Post by artesvida on 2007-05-22
I have an awk command that works perfectly from the command line:

```
awk '$1 ~ /art/ {if (substr($3,2,4)=="find") print substr($3,7,5)}' /path/filename
```

This looks through /path/filename for "art" in the first field, then prints out characters 7 through 11 from the third field if characters 2 through 5 are "find".  So far so good.  Now, I want to put this in a bash script and replace the constant "art" with a variable called USER, and dump the return value into another variable.  This here:

```
VAR=$(awk '$1 ~ /$USER/ {if (substr($3,2,4)=="find") print substr($3,7,5)}' /path/filename)
```

doesn't work.  Of course, because of the single quotes variable substitution isn't happening.  So, I tried this:

```
CMD="awk '\$1 ~ /$USER/ {if (substr(\$3,2,4)==\"find\") print substr(\$3,7,5)}' /path/filename"
VAR=$($CMD)
```

which also doesn't work.  Help!  I'm pretty new to awk and bash; I suspect it's not too hard to get what I want.

Thank you!

---

### Post by ghostdog74 on 2007-05-22
try this:
```

USER="somebody"
result=$(awk -v user=$USER '$1 ~ user {if (substr($3,2,4)=="find") print substr($3,7,5)}' /path/filename)

```

---

### Post by artesvida on 2007-05-22
YES!  Thank you!

---

### Post by Siamang on 2007-05-22
Pipes and backticks can do a decent job too, depends on your personal preference:

```
VAR=`cat /path/filename | awk '/art/ {if (substr($3,2,4)=="find") print substr($3,7,5)}'`
```

Tested this and it produces your specified output. Bash and awk are pretty flexible.


*Edit* - vvvv Cool! vvv

---

### Post by hartz on 2007-05-22
The simplest is to just temporarily pop out of your back-quotes, like this.

```
VAR=$(awk '$1 ~ /'$USER'/ {if (substr($3,2,4)=="find") print substr($3,7,5)}' /path/filename)
```

If you worry about spaces contained in the variable $USER, then use


```
VAR=$(awk '$1 ~ /'"$USER"'/ {if (substr($3,2,4)=="find") print substr($3,7,5)}' /path/filename)
```

---

### Post by ghostdog74 on 2007-05-22
> **Siamang said:**
> Pipes and backticks can do a decent job too, depends on your personal preference:

```
VAR=`cat /path/filename | awk '/art/ {if (substr($3,2,4)=="find") print substr($3,7,5)}'`
```

Tested this and it produces your specified output. Bash and awk are pretty flexible.



[UUOC]("http://www.answers.com/topic/uuoc-computer-jargon")

---

### Post by Siamang on 2007-05-23
I have a terrible habit of doing that. My big problem is that I've picked up UNIX almost entirely through trial-and-error, so while the way I do things work they're hardly the most efficient solution. Thanks for pointing that out.

---

