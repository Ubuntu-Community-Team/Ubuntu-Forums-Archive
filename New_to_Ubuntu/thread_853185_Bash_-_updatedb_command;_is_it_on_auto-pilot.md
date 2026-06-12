---
title: "Bash - updatedb command; is it on auto-pilot?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-08
in the book linux in a nutshell, in linux commands under "locate," it says to update your database with the updatedb command.   However in man it says that it is 'usually' done automatically once per day by cron.  How do I make sure?

---

### Post by camccall on 2008-07-08
If you look under /etc/cron.daily, you can see the script called mlocate, this is the script that updates your slocate(actually mlocate) database in ubuntu.

---

### Post by mcduck on 2008-07-08
It's done once per day automatically, but if you have recently added new files or installed something it wouldn't be in the database so you'd need to run "updatedb" manually before locate can find it.

---

