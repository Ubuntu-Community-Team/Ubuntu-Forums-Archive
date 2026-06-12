---
title: "Lightread: unable to sync after update"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by shankhs on 2012-08-02
Hi,
I updated ubuntu today which included an update to Lightread. After the update,  I started Lightread and its taking forever to sync without any result. 
I am unable to run Lightread from command prompt, so I am not getting any debug message also.
Can anybody please help me to find the solution?

Thanks.

---

### Post by shankhs on 2012-08-02
I found the bug in Lightread LP page which documents the same problem that I am having:
[https://bugs.launchpad.net/lightread/+bug/1029999](https://bugs.launchpad.net/lightread/+bug/1029999)

The bug discussion also mentions a workaround which seems to work for me:

> A workarround is "Sign off" your account and then sign in again. Looks hard to reproduce

Hope it helps somebody!

---

### Post by delki8 on 2012-08-10
I did have to 
1- sing out, 
2- sing in,
3- turn the sync when starts off
4- turn the sync when starts on

And it is solved...

---

### Post by lovinglinux on 2012-08-31
> **delki8 said:**
> I did have to 
1- sing out, 
2- sing in,
3- turn the sync when starts off
4- turn the sync when starts on

And it is solved...

I had the sync problem today and this solved the issue. Thanks.

---

### Post by zeroseven0183 on 2012-10-27
This apparently does not solve the issue if your Google Account has 2-factor authentication enabled. Although you have to sign out and sign in again but you need to re-enroll the application to Google.

---

