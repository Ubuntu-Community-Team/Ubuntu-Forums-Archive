---
title: "sem_open requires root permission"
date: 2008-11-06
forum: Programming Talk
---

### Post by Baer Nase on 2008-11-06
Hi everybody,

we have several Ubuntu 8.04 systems running, and all are up-to-date.
On one of these systems, calls to sem_open as 'normal' user result in an EACCESS error :-(

Any clue what happens? Is there any configuration responsible for this?

Any other forum for this topic?


Thanks

BN

---

### Post by uljanow on 2008-11-06
"ipcs" which shows the owner and permission of semaphores might help.

---

