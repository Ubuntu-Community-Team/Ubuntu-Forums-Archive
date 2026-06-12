---
title: "Cant write to Samba Shares"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by globier on 2012-05-01
Hi All,
   Linux newbie here and I'm a bit stuck.  I have found heaps of posts in the forum with similar issues and have tried all the fixes I have found but have made not forward movement on the problem in 3 days.
So I have ubuntu 12.04 installed with samba and some shares setup which I can see from my windows 7 machine including all files within the shares. However I can not create new files or edit the current files in the shares.

I have setup the linux & Samba user the same as the windows user.
I've set my directory permissions by chmod 775
Here is my smb.conf.
```

[global]
        workgroup = home
        server string = home.com
        netbios name = ubu
        log file = /var/log/samba/%m.log
        log level = 0
        max log size = 150
        socket options = TCP_NODELAY
        security = share

[Test]
        comment = Test
        path = /mnt/test
        read only = no
        create mask = 0775
        guest ok = yes

```
Hope someone can help.
Thanks

---

### Post by Morbius1 on 2012-05-01
You have created a guest share:
        > guest ok = yesA Samba "guest" is a Linux "other".

You set "other" to read only:
> I've set my directory permissions by chmod 775So change permissions to allow "other" to write: chmod 777

---

### Post by globier on 2012-05-02
Thanks, That makes sense.  Worked a treat.

---

