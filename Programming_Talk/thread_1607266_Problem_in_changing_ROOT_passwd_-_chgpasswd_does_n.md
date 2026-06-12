---
title: "Problem in changing ROOT passwd - chgpasswd does not work !? - 10.10"
date: 2010-10-27
forum: Programming Talk
---

### Post by hakermania on 2010-10-27
I always wanted a root passwd, so I gave sudo su, my user passwd and then I typed chgpasswd to set a root passwd and log in as root with simply typing 'su' and root passwd, but nothing happens! I hadn't got this problem in 10.04! What is the prob ? Take a pic to understand better:
[IMG]http://img264.imageshack.us/img264/8742/screenshotewi.png[/IMG]

---

### Post by Barrucadu on 2010-10-27
```
sudo passwd root
```

chgpassword is used (AFAIK) to update passwords in batches - if you want to use it you have to send it the users and passwords on stdin.

---

### Post by hakermania on 2010-10-27
Ok, thx, I was confused between chgpasswd and passwd commands :)

---

