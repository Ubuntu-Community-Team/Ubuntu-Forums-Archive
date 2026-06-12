---
title: "How can I make a folder's name the date in bash?"
date: 2008-08-16
forum: Programming Talk
---

### Post by firebirdworks on 2008-08-16
How can I make a new folder with the date as the name?  Thanks.

---

### Post by bobbocanfly on 2008-08-16
```
mkdir $(date +whatever_format)
```

For example:

```
mkdir $(date +%F)
```

Creates ./2008-08-16/

---

### Post by akudewan on 2008-08-16
```

mkdir "`date`"

```

(The double quotes are for escaping the spaces, and the backquotes are for command substitution)

You can ofcourse use any of the options of the date command

---

### Post by jinksys on 2008-08-16
> **firebirdworks said:**
> How can I make a new folder with the date as the name?  Thanks.


A lot of times **mkdir `date +%F`** is used in conjunction with a crontab, however, if you ever do this make sure you escape the percent sign in your crontab.

```

* * * * * mkdir `date +\%F`

```

You may never have to use this, but I thought I'd throw it out there to save you some time troubleshooting.

---

