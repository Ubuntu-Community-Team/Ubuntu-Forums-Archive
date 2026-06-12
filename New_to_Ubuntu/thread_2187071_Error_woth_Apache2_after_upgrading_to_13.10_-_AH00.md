---
title: "Error woth Apache2 after upgrading to 13.10 - AH00526: Syntax error on line 2 of /etc"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by lee-a-edwards on 2013-11-10
I get the following error when trying to start Apache 2

AH00526: Syntax error on line 2 of /etc/apache2/sites-enabled/leeaedwards.co.uk.conf:
Invalid command 'SuexecUserGroup', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.


I have personally not changed the conf file
Line 2 
states the following:

SuexecUserGroup "#1001" "#1001"

Thanks

---

### Post by ptn107 on 2013-11-10
```
SuexecUserGroup 1001 1001
```
?

---

