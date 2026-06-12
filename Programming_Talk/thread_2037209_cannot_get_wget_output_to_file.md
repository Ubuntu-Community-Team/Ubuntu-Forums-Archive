---
title: "cannot get wget output to file"
date: 2012-08-03
forum: Programming Talk
---

### Post by conradin on 2012-08-03
Hi All I am using wget in spider mode to figure out what sites exist with certain names.

```
wget --spider --tries=1 www.4chan.org >> log
```

as an example. That will run in the terminal and give screen output, but will not put anything in the log file.
Ive tried piping to tee and that was a fail too. 
Can someone help me get the wget --spider output to go to a file?
I am in 12.04

---

### Post by codemaniac on 2012-08-03
> **conradin said:**
> Hi All I am using wget in spider mode to figure out what sites exist with certain names.

```
wget --spider --tries=1 www.4chan.org >> log
```

as an example. That will run in the terminal and give screen output, but will not put anything in the log file.
Ive tried piping to tee and that was a fail too. 
Can someone help me get the wget --spider output to go to a file?
I am in 12.04

specify a logfile with -o switch .

```
wget --spider --tries=1 www.4chan.org -o log.txt
```

---

### Post by sisco311 on 2012-08-04
or with -a to append to the logfile

The messages are normally reported to standard error. ;)

---

### Post by trent.josephsen on 2012-08-04
never mind, I swapped the meanings of -o and -O

---

### Post by conradin on 2012-08-14
Thank you Every one! I used wget --spider --tries=1 [www.4chan.org](www.4chan.org) -a load.log and got file out put. hurray!

---

