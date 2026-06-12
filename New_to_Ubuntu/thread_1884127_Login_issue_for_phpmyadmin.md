---
title: "Login issue for phpmyadmin"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by chisao101` on 2011-11-20
I am having a problem loging in to phpmyadmin. I can go into terminal and log in to mysql that way, but when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I get a login page. When I put in my username and password (same one that works inside terminal mysql), I get an error :#1045 Cannot log in to the MySQL server. 
Is there something I need to change to be able to get in?

---

### Post by lechien73 on 2011-11-20
Have you tried resetting the mysql password, just in case.

```
mysqladmin -u USERNAME password NEWPASSWORD
```

Replace USERNAME with the user you're trying to log in as, and NEWPASSWORD with, obviously, the new password.

---

### Post by chisao101` on 2011-11-21
> **lechien73 said:**
> Have you tried resetting the mysql password, just in case.

```
mysqladmin -u USERNAME password NEWPASSWORD
```Replace USERNAME with the user you're trying to log in as, and NEWPASSWORD with, obviously, the new password.
Hey, thanks...that worked.
I appreciate the help :)

---

