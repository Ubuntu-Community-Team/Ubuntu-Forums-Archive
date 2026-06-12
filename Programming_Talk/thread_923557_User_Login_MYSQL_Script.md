---
title: "User Login MYSQL Script"
date: 2008-09-18
forum: Programming Talk
---

### Post by Greslore on 2008-09-18
Greetings all,

Basically, I have about 20 machines with central authentication (LDAP).  I want to keep track of who is logging in and the date.  And this all needs to be secure.  I am leaning towards going with a MySQL solution.  But I am a bit clueless on this and was hoping someone could point me in the right direction.  

Here is what I am thinking...  
1-Set up MySQL Server
2-Create MySQL User for the logging
3-Create table: USERS
4-Give MySQL User access to the table
5-Create BASH script to place the output of "whoami" and "date" into the USERS table authenticating with the created MySQL user.  This BASH script will be run when the user logs in.  
6-Access MySQL db somehow.

Give me your thoughts if I am on the right track or not.  Likewise, assuming I am indeed on the right track, how exactly do I accomplish parts 5 and 6?  How do I access the MySQL DB?  A script that extracts the data into a text file?  Any help/guidance is MUCHO appreciated!!

---

### Post by drubin on 2008-09-18
> **Greslore said:**
> Greetings all,

Basically, I have about 20 machines with central authentication (LDAP).  I want to keep track of who is logging in and the date.  And this all needs to be secure.  I am leaning towards going with a MySQL solution.  But I am a bit clueless on this and was hoping someone could point me in the right direction.  

Here is what I am thinking...  
1-Set up MySQL Server
2-Create MySQL User for the logging
3-Create table: USERS
4-Give MySQL User access to the table
5-Create BASH script to place the output of "whoami" and "date" into the USERS table authenticating with the created MySQL user.  This BASH script will be run when the user logs in.  
6-Access MySQL db somehow.

Give me your thoughts if I am on the right track or not.  Likewise, assuming I am indeed on the right track, how exactly do I accomplish parts 5 and 6?  How do I access the MySQL DB?  A script that extracts the data into a text file?  Any help/guidance is MUCHO appreciated!!

Pretty cool Idea. But it would not be secure as all! :)

You would include the username/password to the mysql server for each user that has to login.

You could have a web server on the "centeral" server.,
**Edit:** and put this in the clients bash file on the clients side.
```
curl http://server.com/scripts/login.php?u=client1&p=passw
```
u=the user name for this client. (stored in the mysql db, users table)
p=the password for THIS client. (stored int the mysql db, users table)


This way each user does not have direct access to the mysql DB, but only access to a LIMITED interface with the server. Each user has a unique username/password to the server so you may remove that access dynamically.

Take a look at this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

