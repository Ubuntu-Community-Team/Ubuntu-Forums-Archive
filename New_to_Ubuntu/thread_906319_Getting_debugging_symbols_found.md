---
title: "Getting debugging symbols found"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by wankel on 2008-08-31
It happens that a program crashes. For KDE programs, the KDE crash handler will pop up and shows a backtrace. 

Most of the lines in the backtrace say "(no debugging symbols found)".

To let the crash handler find those symbols, can I install a debugging package, or do I need a debug-variant of -for example- Konqueror? Or can't packages with those symbols be installed via apt and do I compile them by hand with debugging on?

I installed "libdebug0", but it does not improve the situation.

Thanks!

---

### Post by thecheatah on 2008-09-02
Try installing kdebase-dbg. I am trying to solve the same problem so I found this package. I am not sure if this will help me since I have fixed the problem which was causing the backtraces, but we will see the next time a kde crash happens.

Also if you search for debug in adept, you will see debug packages for various applications.

---

