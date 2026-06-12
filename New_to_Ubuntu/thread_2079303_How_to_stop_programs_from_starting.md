---
title: "How to stop programs from starting"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by thorbs on 2012-11-01
I have different programs that start up automatically when I start my computer. They are not on the sessions and startup applications lists. 

I think they must have been saved at some point in some startup file, but I dont know where to look. Can anybody help?

---

### Post by Toz on 2012-11-01
Xfce caches sessions so that they can be remembered on next login. When you logout, there is an option to "Save session for future logins".

You can clear these saved sessions, but it depends on the version of Xubuntu you are using: 

12.10 - go to Settings Manager -> Session and Startup -> Session tab, and click on the "Clear saved sessions" button.

12.04 and earlier - you need to manually delete the ~/.cache/sessions folder.

---

### Post by thorbs on 2012-11-02
thanks

---

