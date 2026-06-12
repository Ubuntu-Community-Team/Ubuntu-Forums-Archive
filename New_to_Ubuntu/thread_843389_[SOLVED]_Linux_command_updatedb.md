---
title: "[SOLVED] Linux command: updatedb"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Google Spider on 2008-06-28
When I try to update the database I get:


```
$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'

```

What am I doing wrong?

Thanks

EDIT: sudo....

sorry found the answer. silly me.

---

### Post by robertchahine on 2008-06-28
haha, glad to see that you had resolve your own problem.

---

### Post by mr.circuit on 2008-09-07
I am total newbie ! I have the same problem. How did you solved it ? 

Can you please elaborate ?

---

### Post by drs305 on 2008-09-07
> **mr.circuit said:**
> I am total newbie ! I have the same problem. How did you solved it ? 

Can you please elaborate ?

You run the command as:
```
sudo updatedb
```

If you aren't familiar with sudo, it will ask for your password. As you type you won't see it. Just type it completely and then hit Enter.

Welcome to the ubuntu forums!

---

### Post by yixiong109 on 2009-05-25
[SIZE=3]  [/SIZE][SIZE=3]hellow, I do as you guys advice above, but[/SIZE] [SIZE=4]still met problems as follows:
  " user is not in the sudoers file.  This incident will be reported."
hope skilled guys help me , thank you very much!

[/SIZE]

---

### Post by tr333 on 2009-05-25
You should normally not have to run updatedb as it is run daily via the system cronjob in /etc/cron.daily/mlocate.

---

### Post by tr333 on 2009-05-25
> **yixiong109 said:**
> [SIZE=3]  [/SIZE][SIZE=3]hellow, I do as you guys advice above, but[/SIZE] [SIZE=4]still met problems as follows:
  " user is not in the sudoers file.  This incident will be reported."
hope skilled guys help me , thank you very much!

[/SIZE]

That is telling you that your user account doesn't have permission to use sudo.  You would have to ask the computer administrator to run this for you, or give your account sudo/admin privileges.

---

### Post by javaguru on 2010-09-07
This is because your user doesn't have permissions to write to /var/lib/mlocate/ and it tries to create a temporary file there when you run 'updatedb'

I did the following:```

adyhasch@T60:~/Desktop$ sudo chown adyhasch:mlocate /var/lib/mlocate
adyhasch@T60:~/Desktop$ sudo chmod 775 /var/lib/mlocate/


```
First command changes the owner of the directory to my user, 'adyhasch" ,and the 'mlocate' group

Second, I enable write permissions for the group 'mlocate'

---

