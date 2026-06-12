---
title: "MySQL create user, wildcar host users can't login locally"
date: 2009-11-16
forum: Programming Talk
---

### Post by Sureshot324 on 2009-11-16
If I create a user in mysql with a wildcard host, they are unable to login locally.  I just get an error:
ERROR 1045 (28000): Access denied for user 'myuser'@'localhost' (using password: YES)
If I specify localhost like this:
CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'password'

then they are able to login locally fine.  Is this normal?  If I specify a wildcard host, shouldn't they be able to login from anywhere, including localhost?

---

### Post by januzi on 2009-11-16
Did You run mysql with --skip-name-resolve ? In that case all the host have to be IP number or localhost.

---

### Post by Sureshot324 on 2009-11-19
No I didn't and I don't think that's the problem.  To clarify,

If I create user myuser@localhost, everything works fine
If I create user myuser@% (and drop myuser@localhost) I can't login locally.
If I create both it works, but I don't think I should have to, and on Windows I don't.

Basically it seems like the wildcard isn't working, or at least localhost isn't accepted for the wildcard.

---

### Post by DaithiF on 2009-11-19
do you have an entry in mysql.user where user = '' and host = 'localhost'?
also, can you connect (with only the wildcard host entry present) if you specify host of 127.0.0.1 i.e. mysql -h 127.0.0.1 -u username -ppassword?

---

