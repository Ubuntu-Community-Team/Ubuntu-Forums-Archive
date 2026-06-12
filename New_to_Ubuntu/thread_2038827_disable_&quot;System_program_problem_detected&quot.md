---
title: "disable &quot;System program problem detected&quot;"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by smemamian on 2012-08-07
hi

How do I disable this message?

[CENTER][IMG]http://img4up.com/up2/04775936443462993596.png[/IMG]
[/CENTER]

---

### Post by irv on 2012-08-07
What are you running that is giving you this message? What are you doing when it comes up? This is a message telling you, you have a problem. This is a warning message that something is wrong. You want to fix the problem not get rid of the message.

---

### Post by cmcanulty on 2012-08-07
I too get this on one laptop but nothing seems wrong

---

### Post by irv on 2012-08-07
> **cmcanulty said:**
> I too get this on one laptop but nothing seems wrong

If I remember, awhile back I had something like this and it turned out to be something like compiz crashing. Since then I have done a fresh install so I am not sure if I ever fix it or it just fixed itself after the fresh install?

---

### Post by cmcanulty on 2012-08-07
I too get this on one laptop but nothing seems wrong

---

### Post by smemamian on 2012-08-07
I found :)
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport
```

---

### Post by irv on 2012-08-07
> **smemamian said:**
> I found :)
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport
```

If this works for you and it solved your problem then mark this thread solved.

---

### Post by smemamian on 2012-08-07
ok
Tnx

---

