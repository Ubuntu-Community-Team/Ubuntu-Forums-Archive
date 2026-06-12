---
title: "cronjob?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by auraithx on 2012-05-24
I know this is the lazy way solve this but it's an easy fix until I have time to solve properly.

The MySQL query fixes a small bug in one of my scripts.

Also my site tends to become unusable slow 2-3x a month. I'm installing cache plugins and tidying up all my sites and this amount is reducing. However if I set cronjob to reset the apache every x amount of hours it ensures that if my site goes down while I'm asleep, there's a good chance it'll fix itself


```
GNU nano 2.0.9        File: /tmp/crontab.axbgDC/crontab                      
 
# m h  dom mon dow   command
15 * * * * "/etc/mysql -u root -p passxxx -e "update wp_postmeta set meta_va$
15 * * * * "/etc/mysql -u root -p passxxx -e "update wp_postmeta set meta_va$
0 12 * * * /etc/init.d/httpd restart >/dell/null 2>&1
```

---

### Post by codemaniac on 2012-05-24
So what is your query or it is just for information ?

---

### Post by lukeiamyourfather on 2012-05-24
> **auraithx said:**
> 
```
GNU nano 2.0.9        File: /tmp/crontab.axbgDC/crontab                      
 
# m h  dom mon dow   command
15 * * * * "/etc/mysql -u root -p passxxx -e "update wp_postmeta set meta_va$
15 * * * * "/etc/mysql -u root -p passxxx -e "update wp_postmeta set meta_va$
0 12 * * * /etc/init.d/httpd restart >/dell/null 2>&1
```

Just an observation, did you mean to say /**dev**/null or /**dell**/null in the last line? Also 12 for the hour refers to noon, 0 would be for midnight. Since you mentioned it doing something while you're asleep maybe you meant midnight instead of noon.

---

### Post by auraithx on 2012-05-25
> **codemaniac said:**
> So what is your query or it is just for information ?

Theres something wrong with the syntax causing the commands not to execute - I'm trying to find out what that is.

---

