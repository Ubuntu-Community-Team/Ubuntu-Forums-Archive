---
title: "Basic mysql Setup Questions"
date: 2009-08-08
forum: Programming Talk
---

### Post by tzvi on 2009-08-08
Hello,

I wanted to learn about databases and SQL so I installed mysql 5.0 server, client, admin, and query browser using Synaptic onto my pc.  I am not trying to set up a server or do any kind of development, just wanted to create some tables and run queries on a single pc to learn along in this database book I bought.  The mysql documentation is a little complex, and I'm wondering if anyone can help get me started with this simple setup.

I was able to log into mysql administrator under Server HostName: localhost and User: Root.  Under User Administration, I have three user accounts: Anonymous, debian-sys-maintenance, and root.  What are these for?  What should I be logged in as when working with my database?  How can I/should I create a regular user account for security?

My other question involves the startup of mysql when I turn on my pc.  I believe it is starting automatically as if my pc is a server, but is it possible that I can disable this default and start mysql manually whenever I want to work on it?  The reason is, I think since I installed it, it is sometimes overwhelming my pc where I'm getting system freezes.  I suspect the reason is mysql running in the background, but this is just a speculation.  I would rather not have it start at boot, but let me start it manually whenever I want, then stop it manually when I'm done working with it.

I'm running Ubuntu 8.04.  Any help would be appreciated.  Thanks!

---

### Post by unutbu on 2009-08-08
To add a new mysql user account: Read [http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

The debian-sys-maintenance account is used by mysql for system maintenance. See [http://serverfault.com/questions/9948/what-is-the-debian-sys-maint-mysql-user-and-more](http://serverfault.com/questions/9948/what-is-the-debian-sys-maint-mysql-user-and-more).

I do not know how you got or why you have an Anonymous account.
At least under Intrepid, such an account does not come with a default installation of mysql-server-5.0.

To stop mysqld from running at boot time:
```

sudo update-rc.d -f mysql remove

```
To start the mysql server manually:
```

sudo /etc/init.d/mysql start
```

To stop the mysql server manually:
```

sudo /etc/init.d/mysql stop

```

---

