---
title: "count context switches"
date: 2010-05-18
forum: Programming Talk
---

### Post by Nick188 on 2010-05-18
Hi,
is there anyway to programmatically count context switches of the same process?

thanks.

---

### Post by MadCow108 on 2010-05-18
you could read out the proc folder
/proc/pid/sched
holds your required information.

---

### Post by Nick188 on 2010-05-18
Ok, and if i would use the sar command?? Or the pidstat command??

thanks

---

