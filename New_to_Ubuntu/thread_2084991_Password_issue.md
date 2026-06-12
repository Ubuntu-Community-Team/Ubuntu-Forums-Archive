---
title: "Password issue"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by crestmount on 2012-11-17
For some reason Ubuntu 12.04 won't accept my password anymore.  I try to use upgrade manager and when asked to authenticate, it doesn't happen.  I go to terminal where I am again asked for password--I enter password but it gets rejected.

Basically treating the situation as one where I have forgotten my password (which I haven't)--how do I go about setting a new password without having access to my current password?

---

### Post by Abhinav Kumar on 2012-11-17
> **crestmount said:**
> For some reason Ubuntu 12.04 won't accept my password anymore.  I try to use upgrade manager and when asked to authenticate, it doesn't happen.  I go to terminal where I am again asked for password--I enter password but it gets rejected.

Basically treating the situation as one where I have forgotten my password (which I haven't)--how do I go about setting a new password without having access to my current password?
Hi crestmount,

Are you able to login as root account.
Type the following in terminal
```
sudo -i 
```
and then give the password

:)
Regards,
Abhinav

---

### Post by coldraven on 2012-11-17
I have never tried this but it seems to be what you want.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Gone fishing on 2012-11-17
This thread will help you

[http://ubuntuforums.org/showthread.php?t=2079617](http://ubuntuforums.org/showthread.php?t=2079617)

---

### Post by Wim Sturkenboom on 2012-11-17
> **Abhinav Kumar said:**
> Hi crestmount,

Are you able to login as root account.
Type the following in terminal
```
sudo -i 
```
and then give the password

:)
Regards,
AbhinavOP can always try, but if 'password is rejected on command line' (as stated in opening post), I do not give it much chance :D

---

### Post by crestmount on 2012-11-19
fixed--thanks heaps.  went to terminal and changed password

---

