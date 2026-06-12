---
title: "ant -Dbuild.compiler=gcj BUILD FAILED DateUtils.so ENOENT"
date: 2006-10-08
forum: Programming Talk
---

### Post by Bahco on 2006-10-08
Greetings,

I'm trying to build the cpp tasks from [http://ant-contrib.sourceforge.net/]("http://ant-contrib.sourceforge.net/") using ```
ant -Dbuild.compiler=gcj
```. This results in 

```
BUILD FAILED
.../cpptasks/build.xml:135: Error running gcj compiler
```

Line 135 is within the javac task.

Looking into this with strace, it seems that ant or gcj is looking for a file named ```
lib-org-apache-tools-ant-util-DateUtils.so
``` in the gcj and system library directories. This file is not present on my system, nor can I find it anywhere else. 

I'm running Ubuntu 6.06, and all installed packages are up to date.

Any and all help will be appreciated.

---

