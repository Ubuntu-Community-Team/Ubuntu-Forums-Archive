---
title: "Error when authenticating in Kerberos KRB_AP_ERR_ BAD_INTEGRITY"
date: 2011-05-13
forum: Programming Talk
---

### Post by ibaneight on 2011-05-13
Hi,

i'm trying to use the Kerberos system formy own server, and i've got a problem when trying to authenticate a service with the KDC.

i can add a principal to de databse with the kadmin.local, and if i try to authenticate this principal it works perfectly, but after that i add the same principal to the kerberos Keytab file, and after this operation an error occurs:

KRB_AP_ERR_ BAD_INTEGRITY (31) Integrity check on decrypted field failed - PREAUTH-FAIL

i don't know why this is happening and i hope you can give me some help.

thank you

---

