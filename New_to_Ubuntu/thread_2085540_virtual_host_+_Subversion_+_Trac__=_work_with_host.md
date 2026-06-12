---
title: "virtual host + Subversion + Trac  = work with hosting"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Citromon on 2012-11-18
----

---

### Post by Citromon on 2012-11-18
I tried install again apache and subversion on virtual machin and it works.
In real computer i have this error:

```
apache2: Syntax error on line 260 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/conf.d/svn: /etc/apache2/conf.d/svn:1: <Location> was not closed.
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

---

### Post by pkadeel on 2012-11-18
Try with changing
```
<Location "/svn">
```
to
```
<Location /svn/>
```

---

### Post by Citromon on 2012-11-18
No, it dont help.

/svn mean file "svn", and /svn/ mean folder "svn" in / directory?

---

### Post by Citromon on 2012-11-18
As I wrote, on virtual machine all works good.

I have installed RabbitVCS, php, mysql, phpmyadmin.
What can cause the error?

---

### Post by Citromon on 2012-11-18
Any ideas?

---

### Post by Citromon on 2012-11-19
Can I move this topic here [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) ?

There is only one answer, maybe in Network forum is possible to get more answers.

---

