---
title: "[SOLVED] hellanzb daemon at startup"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by bcd87 on 2008-11-12
Hi :)

How do I get hellanzb to run as daemon at startup?
I know hellanzb -D runs hellanzb as daemon, but how do i get this to be run at startup?

---

### Post by bobbob1016 on 2008-11-12
System->Preferences->Sessions
Add
Name Hellanzb
Command hellanzb
I do that for my cron job, which just runs hellanzb 12am to 6am.  You could make it hellanzb -d if you want, although I haven't used that command.

---

### Post by bcd87 on 2008-11-12
That worked, thanks!

---

