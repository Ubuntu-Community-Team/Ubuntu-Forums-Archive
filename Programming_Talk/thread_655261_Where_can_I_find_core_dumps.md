---
title: "Where can I find core dumps?"
date: 2008-01-01
forum: Programming Talk
---

### Post by khughitt on 2008-01-01
Hey,

I was wondering if anyone might be able to help me figure out where program core dumps go. Several times in the past I've had programs I'm using seg-fault, but i've never been able to find the core files for them. Today the same thing happened while using mysql-admin. I was hoping to find the core file so that I might report the crash, but I'm not sure where to find it. Anyone know where core dumps usually go?

Thanks,

---

### Post by llamakc on 2008-01-01
Instead of showing you how, I recommend you read up on it here:

[http://www.justlinux.com/nhf/Filesystems/Core_Dump_Files_and_What_To_Do_About_Them.html](http://www.justlinux.com/nhf/Filesystems/Core_Dump_Files_and_What_To_Do_About_Them.html)

Be sure you understand any commands before running them.

---

### Post by ghostdog74 on 2008-01-01
do you system find and you will know
```

find / -name "core" -ls

```

---

### Post by stroyan on 2008-01-01
The old way was as described in the link that llamakc pointed to.  The 'ulimit -c' setting that it refers to does affect whether core files are written and how large they are allowed to be.  And the default 'ulimit -c' setting in ubuntu will prevent core files from being written.
But there are new twists to the mechanism.
The newer linux kernel versions will change the names of core files when asked to.  The /proc/sys/kernel/core_uses_pid file or sysctl kernel.core_uses_pid setting can be used to make core file include a process id in their name.  The /proc/sys/kernel/core_pattern file or sysctl kernel.core_pattern setting will cause core files to be written with an arbitrary name or in a different directory.  It can even make core files be piped to a command instead of written to a file.
In fact, ubuntu since the feisty release has included the 'apport' package which will intercept core dumps and create a report in /var/crash/ for core dumps that
occur from programs in an ubuntu package.  The apport process will also create a core file in the current working directory if the 'ulimit -c' setting allows that.

---

### Post by whazooo on 2008-01-02
# /etc/profile
ulimit -S -c 0 > /dev/null 2>&1

---

