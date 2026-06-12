---
title: "reason for hanging"
date: 2006-06-06
forum: Programming Talk
---

### Post by illusion on 2006-06-06
Hey,
 
When starting tomcat server, it takes several minutes to pick up and for pages to be served.  Also when running transactions via spring hibernate to mysql database, hangs at a point in the middle for no apparent reason, then finishes the transaction correctly after a few minutes once again.  The hang occurs between the lines 

 [java] INFO: No TransactionManagerLookup configured (in JTA environment, use of process level read-write cache is not recommended)

<-------------------------------hangs-------------------------------------------------->

[java] 6-Jun-2006 4:22:41 PM net.sf.hibernate.cfg.SettingsFactory buildSett ings

The reason im posting is because It seems to not be related to the programming but something else, especially since the tomcat server is just a matter of downloading and running the startup script, and the same problem may be carrying over in some way when running the transactions.  woindering if its an OS issue, i doublt it but just want to make sure, any feedback on whether tomcat takes several minutes to respond would be useful, which if not the case would mean i have some other problem.  

thanks in advance,
Illusion

---

### Post by nsleiman on 2006-12-14
hi,
did you ever solve this problem?

tomcat on 8180 is just timing out :(

---

