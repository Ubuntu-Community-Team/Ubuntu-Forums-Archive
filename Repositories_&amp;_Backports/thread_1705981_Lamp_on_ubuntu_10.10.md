---
title: "Lamp on ubuntu 10.10"
date: 2011-03-13
forum: Repositories &amp; Backports
---

### Post by norelpy on 2011-03-13
Hi I am using ubuntu 10.10 and I have installed lamp recently. I accidently deleted the /etc/apache2 folder I did not get it back. I tried reinstall apache but the result is same. How can I back it back.

---

### Post by Syirrus on 2011-03-13
> **norelpy said:**
> Hi I am using ubuntu 10.10 and I have installed lamp recently. I accidently deleted the /etc/apache2 folder I did not get it back. I tried reinstall apache but the result is same. How can I back it back.

How exactly did you try to reinstall LAMP?  I assume you tried 

```
sudo apt-get install apache2
```

for just installing apache2 right?

---

### Post by norelpy on 2011-03-13
> **Syirrus said:**
> How exactly did you try to reinstall LAMP?  I assume you tried 

```
sudo apt-get install apache2
```for just installing apache2 right?

I have tried **sudo apt-get install apache2** but this is not working.Then I manually create the apache2 folder via root. But after evry trying to reinstall apache it is empty. The /etc/apache2 folder is still empty

---

### Post by p_j_flynn on 2011-03-21
I did the same thing, Tried removing, reinstalling, creating the directory manually. Eventually solved it.

1. If you have a directory /etc/apache2 then remove it.

2. get aptitude package manager by 

  sudo apt-get install aptitude

3. Now use aptitude to get a fresh copy of apache2

sudo aptitude -y install apache2

Regards

Paul

---

