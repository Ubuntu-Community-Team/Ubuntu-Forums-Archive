---
title: "cron system restore/delete changes"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by james106 on 2014-03-11
Hey, I'm working on a computer that I want to delete all changes every week. But I won't be around to do a clean installation. What's the easiest way to do this?  I have the latest Ubuntu and a little bash experience.

---

### Post by r.stiltskin on 2014-03-11
I'm not sure this is exactly what you had in mind, but it should be easy to delete the user account and home directory and then immediately create a new one with the same username and password.  You can use /etc/skel to save files that you want copied to each new user home directory.  Read manpages for userdel and useradd.

---

