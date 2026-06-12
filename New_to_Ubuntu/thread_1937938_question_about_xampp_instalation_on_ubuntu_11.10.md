---
title: "question about xampp instalation on ubuntu 11.10"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by werty2010 on 2012-03-08
in school we started using xampp and since its available for linux i thought i'll give it try.
but i cant find it in the software center.not sure if im doing something wrong, id like to know which is the correct way to install it...?

please note that i havent done any major changes to my system,doing only the usual updates

---

### Post by wojox on 2012-03-08
You would need to download the [tarball]("http://www.apachefriends.org/en/xampp-linux.html") and build it yourself.

---

### Post by werty2010 on 2012-03-09
> **wojox said:**
> You would need to download the [tarball]("http://www.apachefriends.org/en/xampp-linux.html") and build it yourself.

(as a newbe i ask)isnt there a chanse to break something with the tarball?

---

### Post by wojox on 2012-03-09
Right, you could always install LAMP [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Lars Noodén on 2012-03-09
I would support what wojox has written and suggest that you install the LAMP components the normal way, using the package manager.

perl and a few other things are already on your system by default so you can add the pieces that may be missing:

```

sudo apt-get install openssh-server apache2 php5 mysql-server

```

There are a lot of drawbacks to trying to use XAMPP on Linux. One is that the security updates have to be done manually and don't get the benefit of the package manager (Software Center).  If you use the regular package manager (Software Center, Synaptic, apt-get) then it will track versions and dependencies and allow you to automatically update -- especially security updates.  It will also allow you to uninstall everything cleanly should the occasion arrise.

---

### Post by werty2010 on 2012-03-09
if i was to do the whole thing with terminal,what should i type besides 
"sudo apt-get install openssh-server apache2 php5 mysql-server" ?

(i cant find lamp on soft. center)

---

### Post by Lars Noodén on 2012-03-10
> **werty2010 said:**
> if i was to do the whole thing with terminal,what should i type besides 
"sudo apt-get install openssh-server apache2 php5 mysql-server" ?

(i cant find lamp on soft. center)

That would be enough.  Perl is built in.  Remember LAMP stands for Linux, Apache, MySQL, and Perl.  Sometimes Lighttpd or nginx is substituted for Apache, sometimes Postgresql is substituted for MySQL, sometimes python or PHP is substituted for perl. They're all in the repository and together they comprise LAMP.

---

