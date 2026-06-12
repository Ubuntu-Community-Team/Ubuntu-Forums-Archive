---
title: "create new users, permissions, etc."
date: 2011-09-14
forum: New to Ubuntu
---

### Post by richyrage on 2011-09-14
Hello Again All!!!

How would I create a new user with this setup:

'create a user in the www-data group that has a home folder of /var/www'

-from what I gather there is the adduser and the useradd commands, and I am unsure 
what the difference is between the two...

-also from what I read since I will be the only developer, I would like to be the 
sole owner ---would that be something like  $ sudo chown /var/www/

-lastly, how to 'set permissions to 755 for directories and 644 for files' so I can
login to the server as the new user and have full permissions to edit stuff on 
/var/www using PSFTP, because atm when I try to 'put' a new index.html on the server I get a permissions error?

Thanks a bunch!!!

RR

---

### Post by gnometorule on 2011-09-14
adduser adds a new user; useradd adds a user to a group. You change ownership using chown. Instead of giving you 'copy and paste' answers for your immediate question, you should read the man pages of these commands, plus go over this page (or a similar one):

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

Linux/Ubuntu is learning by figuring things out as well. This is an easy question for you (after you read the above link), and it'll be both more helpful long-run and more satisfying if you get it yourself. :)

---

### Post by richyrage on 2011-09-14
gnometorule

thanks for leading me to the right direction

regards,
RR

---

