---
title: "kmysqladmin login help"
date: 2007-04-29
forum: Programming Talk
---

### Post by Ranganaths on 2007-04-29
Hi all,

    I  installed the kmysqladmin from the synaptic manager. I want to know the userame and password to be used to login to this kmysqlamdin. In command interface i am able to login only using the following command "sudo mysqladmin"  then the system asks for the password and after that  i am able to log in. But with the kmysqladmin  gui interface i would like to know how to login.

        Help in this regard will be highly appreciated.


Thank you

---

### Post by kano on 2007-04-30
Have you set a password for your root mysql user? If not, just File->Connect to SQL Server, then Host: localhost, User: root, no password, and the port is 3306.
Otherwise, the root password will be whatever you set it to when you setup MySQL.

---

