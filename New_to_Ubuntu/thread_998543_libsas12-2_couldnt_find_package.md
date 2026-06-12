---
title: "libsas12-2 couldnt find package"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by 007casper on 2008-11-30
server set up 8.10

[http://howtoforge.com/perfect-server-ubuntu-8.10-p5](http://howtoforge.com/perfect-server-ubuntu-8.10-p5)

in the terminal typed 
```
apt-get install postfix libsas12 sas12-bin libsas12-modules procmail
```

I get 
E:Couldn't find package libsas12-2

I found out that libsas12-2 is suppose to be libsasl2-2 (with an L letter not 1)
[http://ubuntuforums.org/showthread.php?t=588658&highlight=libsas12-2](http://ubuntuforums.org/showthread.php?t=588658&highlight=libsas12-2)

the rest of the command is with L and not with 1 right... such as sasl2-bin libsasl2-modules procmail... etc

right?

---

### Post by adult swim on 2008-11-30
they are all L's

---

### Post by 007casper on 2008-11-30
thank you

cheers

---

### Post by sasdaman on 2009-09-08
Thanks this resolved my issue too!

Many thanks

---

