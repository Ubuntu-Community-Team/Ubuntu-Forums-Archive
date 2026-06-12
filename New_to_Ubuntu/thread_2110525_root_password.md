---
title: "root password"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by tomzie on 2013-01-30
Hi, I have just installed the Ubuntu Server 12.04.1 in Virtual Box 4.1.12 successfully. I have created a new user test/test123. I am able to login as test/test123, but what is my root password? I was not asked for root password. Thanks.

---

### Post by steeldriver on 2013-01-30
Hello and welcome - please have a read of this link, it explains how root works under Ubuntu

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2013-01-30
> **tomzie said:**
> Hi, I have just installed the Ubuntu Server 12.04.1 in Virtual Box 4.1.12 successfully. I have created a new user test/test123. I am able to login as test/test123, but what is my root password? I was not asked for root password. Thanks.

root doesn't have a login or account under the default ubuntu.
You can become root by using sudo from an account authorized to use sudo.

$ sudo -s

---

### Post by lisati on 2013-01-30
Please read the information at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

