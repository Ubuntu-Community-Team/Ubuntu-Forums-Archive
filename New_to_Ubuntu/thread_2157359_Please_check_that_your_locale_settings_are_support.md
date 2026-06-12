---
title: "Please check that your locale settings are supported or installed on your system."
date: 2013-06-25
forum: New to Ubuntu
---

### Post by SharpMelon on 2013-06-25
Hello Ubuntu users, recently I decided to switch over to Ubuntu and when I was installing a few packages I noticed I got an [error]("http://i.imgur.com/Vvqp14t.png"). I am sure this question have been asked like a million times but why does this appear and is there a way to solve the issue? I feel like I have tried everything to get rid of it but it just does not work. I am clearly doing something wrong here. This is probably irrelevant but I tried reinstalling Ubuntu and I got the same type of [message]("http://i.imgur.com/Vvqp14t.png") (I am using Ubuntu Server 13.04 64 bit). Help is much appreciated.
```
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

---

### Post by siddharth007 on 2013-06-27
You need to open the file /etc/environment and add this line
```
LC_ALL="en_US.utf8"
```

Save the file and reboot your system.This should solve your problem.

---

