---
title: "smbpasswd question"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by ubunnewbie on 2013-01-14
Hi,

Is it possible to somehow use the current logged in user and then just set the password?

```
sudo smbpasswd -a "current user"
```

So if 'Bob' is currently logged in, Bob will be used and I will just have to create the Samba password for Bob. I'm trying to write a script to automate the process of installing Samba. Thank you for your time everyone!

---

### Post by bab1 on 2013-01-15
> **ubunnewbie said:**
> Hi,

Is it possible to somehow use the current logged in user and then just set the password?

```
sudo smbpasswd -a "current user"
```

So if 'Bob' is currently logged in, Bob will be used and I will just have to create the Samba password for Bob. I'm trying to write a script to automate the process of installing Samba. Thank you for your time everyone!

The *bash* variable you need is $USER.  If you use the echo command you will see the current logged in user.  See the output of this```
echo $USER
```

---

