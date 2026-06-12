---
title: "Bash command to determine Ubuntu version number"
date: 2008-05-16
forum: Programming Talk
---

### Post by t-molli on 2008-05-16
Hi,

Anyone know the bash command that would allow you to determine what version of Ubuntu (7.04, 7.10, 8.04) you are using.

I want a script to:

check version number and 

if ubuntu 7.04

then

elsif ubuntu 7.10

then

elsif ubuntu 8.04

then

elsif none of the above

then exit

thank you very much in advance...

---

### Post by tseliot on 2008-05-16
Type this command:
```
lsb_release -r
```

and you will get something like this:
```
Release:	8.04
```

---

### Post by LaRoza on 2008-05-16
```

cat /etc/issue

```

(also)

---

### Post by goldcaddy77 on 2013-02-10
You can also run this  command:

```
. /etc/lsb-release
```...and the following variables would be opened up in your script:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
```

---

### Post by CharlesA on 2013-02-10
Good command, but this thread is from 2008 and is going back to sleep. :)

---

