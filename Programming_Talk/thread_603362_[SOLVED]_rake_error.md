---
title: "[SOLVED] rake error"
date: 2007-11-05
forum: Programming Talk
---

### Post by frietzieey on 2007-11-05
i was trying to create tables by running rake db::migrate but encountered this :
     fritzie@place-desktop:~/social_graph$ rake db::migrate
     (in /home/fritzie/social_graph)
     rake aborted!
     Don't know how to build task 'db::migrate'

     (See full trace by running task with --trace)

couls anyone help me what to do next?thanks

---

### Post by jespdj on 2007-11-05
Try
```
rake db:migrate
```
with a single colon instead of db::migrate with a double colon.

[http://wiki.rubyonrails.org/rails/pages/UnderstandingMigrations](http://wiki.rubyonrails.org/rails/pages/UnderstandingMigrations)

---

### Post by frietzieey on 2007-11-05
> **jespdj said:**
> Try
```
rake db:migrate
```
with a single colon instead of db::migrate with a double colon.


thanks so much, if you did'nt reply i would not realize that indeed its supposed to be one colon only.. whew..my mistake:D

---

