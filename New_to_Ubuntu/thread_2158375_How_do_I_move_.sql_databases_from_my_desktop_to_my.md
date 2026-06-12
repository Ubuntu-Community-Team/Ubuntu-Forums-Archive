---
title: "How do I move .sql databases from my desktop to my cloud server"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by dustinnay on 2013-06-28
I've been hosting on a managed cloud server system using Cent OS and I'm migrating this to some new (self-managed) cloud servers I've set up on Digital Ocean. They are running Ubuntu 12.04 64-bit edition. I'm relatively new to CLI, but I've been learning for the past 6 weeks (this is my first forum post though): setting up LAMP, installing WordPress, etc.

But I need to migrate several websites from my old hosting (all WordPress except a couple static sites, but those are easy). I've been able to set up a new WordPress install just fine. But importing and correctly configuring existing databases is still baffling. I've searched Google extensively and found bits and pieces.

I have WinSCP and Filezilla installed, and I've been using PuTTY to access the server in command line. I do NOT have command line access to my old server (FTP access only to the site file directory).

My questions:

1) Where do I import the .sql to? Is there a specific directory where I need to upload them? The folders I've tried looking at via SFTP for mysql are all assigned to the mysql user, and I don't believe I can access that except locally (after logging in with my user account). I've also disabled remote login for root user for security.

2) How do I configure the database once it is uploaded? Or do I need to do anything? (I'm assuming I have to do something with user permissions/password because those settings are from the old server)...

Once I have those taken care of, I know how to set up the wp-config file to call the DB correctly. Just getting there is my dilemma.

Hopefully that all made sense...

Thanks in advance,

--sys admin n00b


PS: I'm moving tonight/tomorrow, so I may not see responses again until Monday, but again, thanks in advance.

---

### Post by Cheesemill on 2013-06-28
You really need command line access to your old server so you can dump the database correctly. Once you have this you would use the following command...
```
mysqldump -u root -p <PASSWORD> --all-databases > databases.sql
```
This will create a file called databases.sql that contains all of the sql commands needed to recreate your databases, copy this file onto your new server.

To load the backup onto your new server you would then do...
```
mysql -u root -p <PASSWORD> < databases.sql
```

---

