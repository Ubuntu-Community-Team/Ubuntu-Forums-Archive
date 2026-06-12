---
title: "expression only showing time"
date: 2020-12-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-17
running 20.04
the below outputs time only would like to include the date
echo "job finished @$(date +'%T')"
below example output
job finished @14:57:44
tks

---

### Post by #&amp;thj^% on 2020-12-17
Will this work:
```
$ echo "job finished @$('date' +'%D%Y')"
job finished @12/17/202020

```
Or your example:
```
echo "job finished @$('date' +'%D %T')"
job finished @12/17/20 14:33:43

```

---

### Post by yancek on 2020-12-17
You need to indicate the month, day and year in the script as below.  Change the order if you don't want month first, etc.  There are many tutorials available on line discussing the date command.

```
 #!/bin/bash
echo "job finished on $(date +"%m-%d-%Y @%T")" 
```

---

### Post by rburkartjo on 2020-12-17
tks yan that did the trick

---

