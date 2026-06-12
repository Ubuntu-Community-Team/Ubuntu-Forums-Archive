---
title: "MySQL help!"
date: 2007-05-09
forum: Programming Talk
---

### Post by derby007 on 2007-05-09
I was trying to change my root password for my MySQL account, i ssued the command : 'update user set password='xxx' where user='me'; but i think i should have used 'set password=PASSWORD('xxx')'. So.....I now cannot access MySQL at all !!!!! pls help, is there a way to get my account back, or am I stuck with a reinstall, nooooooo  :(

---

### Post by LaRoza on 2007-05-09
Does the old or new password work?

What happens if you add the same quotes you used to make the password?

Can you log in as a different user?

---

### Post by yaaarrrgg on 2007-05-09
this might work:

[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

Also, you might look at the GRANT syntax for updating/adding user roles.  It's a bit easier to use than direct manipulation of the tables ...

---

### Post by derby007 on 2007-05-09
Yes, excellent stuff....(or in Irish: get up da yard ye good thing)  :)

---

