---
title: "Questions about ssh."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-11-16
So I've been learning quite a bit about ssh recently, I've played with it a bit, and overall it seems pretty cool.  Despite this, I have been troubled by the idea of some one remotely logging onto any of my computers and pretty much doing anything they want.  Let's say hypothetically, that some weird things have been happening with my computer and I don't know why, could I some how figure out who/what is causing it if it is in fact some punk via an ssh connection?

---

### Post by jimmy the saint on 2008-11-16
[http://ubuntuforums.org/archive/index.php/t-13674.html](http://ubuntuforums.org/archive/index.php/t-13674.html)
check out that thread

---

### Post by jrothwell97 on 2008-11-16
You should be safe as long as you have a strong password, and only enable ssh authentication for your own account.

---

### Post by bettlebrox on 2008-11-16
If said punk is a good cracker you'd have a hard time finding traces of their activities as they'd remove all trace from any/all of the log files and be able to hide any processes they're running. 

There are ways to make ssh more secure than the default install (google it, there are plenty of tutorials) and install and configure the [fail2ban]("http://www.howtoforge.com/fail2ban_debian_etch") package and make sure you use a secure password (so it's not vulnerable to a [dictionary]("http://en.wikipedia.org/wiki/Dictionary_attack") attack).

And make a back-up copy of any configuration files before you make any changes. :)

---

### Post by eldragon on 2008-11-16
if you are only connecting through one given laptop, you could always enable priv/pub key auth, which is far more secure. then disable password login altoguether.

fail2ban is a must if you wish to open ssh or any other port to the world.

---

