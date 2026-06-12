---
title: "best way to do mysqldump programatically"
date: 2011-05-29
forum: Programming Talk
---

### Post by badperson on 2011-05-29
Hi,
I have a java jsp/servlet web app running on my home server that connects to a mysql database. I have system where I can dump the data as xml (my own schema) but I would also like to be able to do a weekly mysqldump. 

Can I do this in a bash script without having to manually enter the pw for ubuntu and the pw for mysql? 

Also, is it best to do that kind of thing in a bash scipt, a separate server admin kind of function? Or should it be done from the java app? 

thanks!
bp

---

### Post by LoneWolfJack on 2011-05-29
```
mysqldump -u<username> -p<password> -Ace | gzip > dbdump.txt.gz
```

doesn't really matter from where you run this command.

---

### Post by Some Penguin on 2011-05-29
[http://www.techiecorner.com/1619/how-to-setup-mysqldump-without-password-in-cronjob/](http://www.techiecorner.com/1619/how-to-setup-mysqldump-without-password-in-cronjob/)

seems relevant.

---

