---
title: "Copying file to destination: how to preserve directory hierarchy?"
date: 2009-11-15
forum: Programming Talk
---

### Post by MacUntu on 2009-11-15
I have a text file containing a list of files like:

```
/etc/modprobe.d/blacklist.conf
/etc/rsyslog.d/50-default.conf
/etc/ufw/ufw.conf
/lib/bootchart/gather
/lib/resolvconf/list-records
/usr/lib/php5/20060613+lfs/gd.so
/usr/lib/php5/20060613+lfs/pdo.so
```

How would I copy them to a target directory while keeping the directory hierarchy intact?

I can't do ```
for file in list: cp file target
``` because that would put all files in the target directory.

I also cannot do ```
for file in list: cp file target/file
``` because direcotries like /etc or /usr/lib/php5 don't exist.

Any help is appreciated, TIA!

---

### Post by Arndt on 2009-11-15
> **MacUntu said:**
> I have a text file containing a list of files like:

```
/etc/modprobe.d/blacklist.conf
/etc/rsyslog.d/50-default.conf
/etc/ufw/ufw.conf
/lib/bootchart/gather
/lib/resolvconf/list-records
/usr/lib/php5/20060613+lfs/gd.so
/usr/lib/php5/20060613+lfs/pdo.so
```

How would I copy them to a target directory while keeping the directory hierarchy intact?

I can't do ```
for file in list: cp file target
``` because that would put all files in the target directory.

I also cannot do ```
for file in list: cp file target/file
``` because direcotries like /etc or /usr/lib/php5 don't exist.

Any help is appreciated, TIA!

Perhaps the program 'cpio' can help.

---

### Post by sisco311 on 2009-11-15
```
cp --parents source target
```

---

### Post by MacUntu on 2009-11-15
> **Arndt said:**
> Perhaps the program 'cpio' can help.

Thanks, why don't I know about that program? :D Unfortunately it creates all directories with the user running cpio (while preserving ownership of the files).

> **sisco311 said:**
> ```
cp --parents source target
```

That's it! Thanks, seems I misinterpreted '--parents'. :)

---

