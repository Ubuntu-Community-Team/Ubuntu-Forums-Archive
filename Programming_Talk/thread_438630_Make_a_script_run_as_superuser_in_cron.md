---
title: "Make a script run as superuser in cron"
date: 2007-05-09
forum: Programming Talk
---

### Post by Biochem on 2007-05-09
I want to make a script that would require superuser privilege. But the script will  be run by cron so I wont be there to enter the password. Is there a way to do that?

---

### Post by xtacocorex on 2007-05-09
You could put the script in the system cron and not your user cron, those are run with root privileges.

---

