---
title: "GET , POST and REQUET not working"
date: 2009-07-16
forum: Programming Talk
---

### Post by arajapandi on 2009-07-16
Hi Everyone,

I installed apache,php, mysql ( [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) )

but when i submit the form i can't get the form values. all values r empty.

plz help me to resolve this problem?

---

### Post by t4thfavor on 2009-07-17
Consider moving this to the developers forum, it tends to get buried slower.
Also think about perhaps posting a bit more information, like your script....

---

### Post by L815 on 2009-07-17
Some code to look at would help us debug your problem :]


Did you check to see if the server is working? ([http://localhost](http://localhost))
If it does, did you put your web pages in /var/www (I think that's the location)

---

### Post by arajapandi on 2009-07-21
Hi L815/t4thfavor,

Thank you for your reply.

I changed the session life time to 84000 in php.ini .. that's the problem i figured out and changed to 14000 now its working. 

```
session.gc_maxlifetime = 84000 
```

---

