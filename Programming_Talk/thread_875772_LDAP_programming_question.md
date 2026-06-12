---
title: "LDAP programming question"
date: 2008-07-31
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-31
Hi! I am programming using <ldap.h>. I've got the following problem: Every time I use a command like ldap_create() or ldap_open() or ldap_initialize() etc., I compile the program without problems. The when I start it, it doesn't'work properly and in /var/log/messages I read :"undefined symbol: ldap_create"

Thanks in advance

---

### Post by henchman on 2008-07-31
Have you linked against the corresponding library? which compiler are you using?

if you are using gcc, then try

```

gcc foobar.c -lldap

```

this should work

---

### Post by blooddrunk on 2008-07-31
Thank you!

---

### Post by blooddrunk on 2008-08-04
I've done what was proposed above and it works but only for some of the functions in <ldap.h>. It still gives me "undefined symbol" for functions like ldap_kerberos_bind_s, for example. What should I do?

---

### Post by KingTermite on 2008-08-04
> **blooddrunk said:**
> I've done what was proposed above and it works but only for some of the functions in <ldap.h>. It still gives me "undefined symbol" for functions like ldap_kerberos_bind_s, for example. What should I do?

It sounds like whatever you are using for a reference might be using functions of a newer version of the library. You should check and see if the library on your machine (as well as header files) are the latest.

---

### Post by blooddrunk on 2008-08-04
I did. And the funny thing is all that functions are in the library

---

### Post by KingTermite on 2008-08-04
> **blooddrunk said:**
> I did. And the funny thing is all that functions are in the library

Are you sure there isn't another (older version) on the machine that is also in your libpath (and before the location of your other one)?

---

### Post by blooddrunk on 2008-08-05
I am not sure. How can I check that?

---

