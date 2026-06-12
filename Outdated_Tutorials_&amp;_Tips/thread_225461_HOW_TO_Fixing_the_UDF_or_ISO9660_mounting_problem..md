---
title: "HOW TO: Fixing the UDF or ISO9660 mounting problem."
date: 2006-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ovimunt on 2006-07-29
***Posted on 29/07/2006 23:42 GMT.***

The right solution to this problem is a lot easier that anyone may have thought.

First, open your ***fstab*** file for editing (in super user mode). Depending on your GUI use the appropriate command:

***Gnome:***
```

sudo gedit /etc/fstab

```
***KDE:***
```

sudo kate /etc/fstab

```
Look for a line similar to this:
```

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```
Replace the ***udf,iso9660*** bit with ***auto***, i.e.
```

/dev/hdc /media/cdrom0 auto user,noauto 0 0 

```
Save the file.

That's it, now all should be fine!

---

### Post by N008 on 2007-07-26
before i did that i got this:

[[IMG]http://img401.imageshack.us/img401/9300/screenshotgnomemountpt9.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshotgnomemountpt9.png)

and now i get this:

[[IMG]http://img508.imageshack.us/img508/6989/screenshotgnomemount1aw0.th.png[/IMG]](http://img508.imageshack.us/my.php?image=screenshotgnomemount1aw0.png)

What should i do?

---

