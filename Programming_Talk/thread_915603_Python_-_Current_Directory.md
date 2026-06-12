---
title: "Python - Current Directory"
date: 2008-09-10
forum: Programming Talk
---

### Post by nebu on 2008-09-10
Is there a way to get a list of all the files (of a particular extension) in a directory using python

---

### Post by Def13b on 2008-09-10
One option is the glob module,

[http://docs.python.org/lib/module-glob.html](http://docs.python.org/lib/module-glob.html)

There is also a handy section on glob in the Dive into Python book (google or /usr/share/doc/diveintopython if your on ubuntu)

---

### Post by The Cog on 2008-09-10
look at the os module, esp. os.listdir(dirname) and os.path.walk(top, func, arg)

---

### Post by skeeterbug on 2008-09-10
sys.path[0] will give you the current directory.

Example:
log = os.path.join(sys.path[0], "dev.log")

---

### Post by days_of_ruin on 2008-09-10
> **The Cog said:**
> look at the os module, esp. os.listdir(dirname) and os.path.walk(top, func, arg)I think os.path.walk is deprecated, use
os.walk instead.

---

