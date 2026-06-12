---
title: "Sql for lubuntu?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by RAJASD on 2011-10-14
I am using lubuntu.i want sql for simple usage.im not expert
in sql.just for preparing exam.

is there any?

if it is there, tell me how to install thru terminal(apt-get like that)?

should i use sql with terminal only or i can get a interface 
for the command line?

tell me simple one with no difference with stable sql...

come on guys ive exam tomorrow;)

thank you..:)

---

### Post by aeiah on 2011-10-14
mysql and postgresql are in the software repository. you can interact via queries on the command line. the common thing to do though is to also install phpmyadmin, so you can see things visually and administer things better. its probably simplest if you install LAMP (linux, apache, mysql, php). there are plenty of tutorials for this

see here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

commands are
```

sudo apt-get install tasksel
sudo tasksel install lamp-server
```

---

### Post by RAJASD on 2011-10-14
thanks bro...

---

### Post by RAJASD on 2011-10-14
> **aeiah said:**
> mysql and postgresql are in the software repository. you can interact via queries on the command line. the common thing to do though is to also install phpmyadmin, so you can see things visually and administer things better. its probably simplest if you install LAMP (linux, apache, mysql, php). there are plenty of tutorials for this

see here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

commands are
```

sudo apt-get install tasksel
sudo tasksel install lamp-server
```

i installed the code u told me.i worked sql in windows.i can directly go to sql and work onit.
where should i go to run sql in lubuntu? in terminal?
sql.

---

