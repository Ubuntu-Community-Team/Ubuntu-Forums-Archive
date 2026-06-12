---
title: "How to clear the warning about clock?"
date: 2012-08-09
forum: Programming Talk
---

### Post by pellyhawk on 2012-08-09
While compiling a project with g++ or gcc, a warning often emerged. What does this warning mean and how to deal with it? 

```
make: warning:  Clock skew detected.  Your build may be incomplete.

```

Thanks.

---

### Post by dwhitney67 on 2012-08-09
Pretty much it means that you have source files or object files that have been moved from one system to another, where each system has a different time, and hence the files have a time-stamp that is in the "future" relative to the time of the destination system. 

Make looks at the time-stamps of files, not their contents, to decide whether a file needs to be processed.

Fix your system time to be in sync with the other system (consider using [NTP]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server") on both systems), or after you have copied files from one system to another, "touch" them so that their time-stamps are updated to the destination system's time.

P.S.  The files do not necessarily have to be moved from one system to another; their time-stamps can be adjusted manually as well.  But typically the issue arises when files are copied.

---

