---
title: "MySql Instance Management"
date: 2007-10-22
forum: Programming Talk
---

### Post by shoaibnawaz on 2007-10-22
How to check the running instances of mysql?
I have installed following my sql packages:

> 
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu2                       
ii  libdbd-mysql-perl                          3.0008-1build1
ii  libmysqlclient15off                        5.0.38-0ubuntu1.1
ii  mysql-admin                                1.2.5rc-1
ii  mysql-admin-common                         1.2.5rc-1
ii  mysql-client-5.0                           5.0.38-0ubuntu1.1
ii  mysql-common                               5.0.38-0ubuntu1.1
ii  mysql-query-browser                        1.2.5beta-3ubuntu4
ii  mysql-query-browser-common                 1.2.5beta-3ubuntu4                    
ii  mysql-server                               5.0.38-0ubuntu1.1
ii  mysql-server-5.0                           5.0.38-0ubuntu1.1
ii  php5-mysql                                 5.2.1-0ubuntu1.4
ii  python-mysqldb                             1.2.1-p2-4ubuntu4


now whenever I try to connect to MySql server instance using mysql-admin specifying Host as "localhost", username as"root", port as "3306" and empty password then following message appears:

> Could not connect to host 'localhost' MySql Error Nr. 1045
Access Denied for user 'root@'locahost'(using password: NO)

I have not defined password yet.

---

