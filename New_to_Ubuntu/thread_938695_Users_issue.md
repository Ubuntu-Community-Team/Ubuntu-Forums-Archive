---
title: "Users issue"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-05
Hi!!! Very newbie user question

I have just installed Ubuntu 8.04, with the installation user A.

Now, I've installed postgresql in order to do some database stuff. You know that it requires to add a user "postgres" into the system. I've done that. Of course this new user doesn't have all the software that A has (eclipse, java etc).

Is there any way that "postgres" user can access to all the files of the user A?

My idea is, I want to edit sql files within the A account with the editors I've installed. Then just switch to postgres, enter posgresql, and run the sql files (which will be on the /home/A/scriptssql) ...

Any idea??

Or I should install within postgres user all software and work there ?

---

### Post by ggaaron on 2008-10-05
If it's a testing environment, why bother with the postgres user? Can't you run PostgreSQL as your A user? Second, how did you install the packages so they are not global and only A user can access them?

---

### Post by fredscripts on 2008-10-05
Thanks for answering!!!


Well the installation instructions of my postgresql version told me to create and use the postgres user. I will try to work with the A user though.

---

### Post by ggaaron on 2008-10-05
And why didn't you install it using apt? It should run as a different user in production environment, but for testing and developing it might be easier to run it as normal user.

---

### Post by fredscripts on 2008-10-05
Well actually I need an old version of posgresql 7.4.18 which isn't on apt-get list because the current is more than 8. College stuff...

Will try to get rid of that postgres user hehe

---

### Post by fredscripts on 2008-10-05
Seems postgresql have needs that special postgres user...because working with my normal user crashes with permisions and stuff (even with sudo...). Nevermind will work under postgres user.

---

### Post by ggaaron on 2008-10-06
You must be able to run postgres as a different user, I'm sure I've done it. It was some time ago and I've done only basic things so I can't provide more information=( Search the web, I'm sure something will come out (a needed switch, a config file as with apache or something similar).

---

