---
title: "MySQL Password"
date: 2007-04-26
forum: Programming Talk
---

### Post by md5hash on 2007-04-26
i just installed mysql from synaptic.. now how can i set the root password...:popcorn:

---

### Post by patjoh on 2007-04-26
Hi!
Open a terminal and run the following commands:
[I]sudo mysqladmin -u root password newrootsqlpassword
sudo mysqladmin -p -u root -h localhost password newrootsqlpassword[/I]

where newrootsqlpassword is the password you want to use for this user.

If you have forgotten your mysql password, read this: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

Cheers!

---

### Post by md5hash on 2007-04-26
thanks for the quick reply..

---

