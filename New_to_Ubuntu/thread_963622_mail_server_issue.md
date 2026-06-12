---
title: "mail server issue"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Mansoor Ahmed on 2008-10-30
i have configured a mail server on ubuntu using postfix-dovecot-squirrelmail. im not using LDAP or SQL, using simple file to store virtual user password and user ID. 

Now the problem is that im unable to chage the password of user from squirrelmail (i have change_password plugin) it is showing link in options to change password but when i do so it returns error

[COLOR="Red"]An error has occurred while attempting to change your password. Please contact your system administrator.
Command output: 
chpasswd - setuid: Operation not permitted
Return code: 1[/COLOR]

---

### Post by Het Irv on 2008-10-30
I am not familiar with what you are trying to do... but at a glance it looks to me like you don't have the nessicary permissions to change the password.  I know this doesn't help much, but it might get you on the right track.

---

