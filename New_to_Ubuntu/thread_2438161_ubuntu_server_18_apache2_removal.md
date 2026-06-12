---
title: "ubuntu server 18 apache2 removal"
date: 2020-03-06
forum: New to Ubuntu
---

### Post by cnedas on 2020-03-06
Hello,

I removed Apache2 from Ubuntu Server 18 with:

```
apt remove apache2
apt autoremove
apt-get  --purge remove "apache*"
```

I do everything again and I get the alert that Apache is not installed and there is nothing to remove.

I try to install Vesta CP and I get an alert that Apache2 package is installed.

I do: 

```
whereis apache2
```
 
and I get:

```
apache2: /etc/apache2
```

So, how come it is at /etc/apache2 but I algo get a "nothing to remove"?

Any suggestions?

---

### Post by CelticWarrior on 2020-03-06
Hoe did you install Apache in the first place is the question...

If you haven't used APT then APT doesn't know about it.

---

### Post by deadflowr on 2020-03-06
/etc/apache2 holds configuration files for other packages beside apache2.
I know javascript-common has the file /etc/apache2/conf-available/javascript-common.conf in it.

---

