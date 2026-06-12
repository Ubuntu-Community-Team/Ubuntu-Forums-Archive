---
title: "mysql"
date: 2007-01-27
forum: Programming Talk
---

### Post by Ranganaths on 2007-01-27
HI guys,

With your great support i am getting use to ubuntu now. Again i need to seek all your help.
 how to install the mysql, I use it for every thing like  java,jsp,struts,spring,hibernate,swings,python

Thank you
Regards

---

### Post by Titus A Duxass on 2007-01-27
sudo aptitude install mysql-server, mysql-client mysql-common

---

### Post by phossal on 2007-01-27
As an alternative. :)
```
sudo apt-get install mysql-server mysql-client
```

---

### Post by Medieval_Creations on 2007-01-27
Another useful tool for MySQL is phpMyAdmin.  It's a webbased front end to MySQL.  I use it when I'm being lazy and don't want to use the CLI :)

```
sudo apt-get install php5 phpmyadmin
```

---

### Post by Ranganaths on 2007-01-27
fine, I also need to know how to access the mysql after the installation. I am new to mysql on Linux. Please give me the steps 

 I have installed this web based front end also. let me know how to use it.

[COLOR="Red"]"Another useful tool for MySQL is phpMyAdmin. It's a webbased front end to MySQL. I use it when I'm being lazy and don't want to use the CLI"
Code:
sudo apt-get install php5 phpmyadmin[/COLOR]



thanks a lot guys.. Ubuntu team is doin great job! keep it up!

---

### Post by phossal on 2007-01-27
If you're new to MySQL, you probably want to get a good book on it, and [read the documentation]("http://dev.mysql.com/doc/refman/5.0/en/index.html") in the meantime. MySQL is very well documented. 

To access mysql from the command line:
```
mysql -u root
```

I don't like phpadmin when I'm administrating mysql on my *own* computer. It's usually faster and easier to use the terminal.

---

### Post by Medieval_Creations on 2007-01-27
To get to phpMyAdmin, just open your preferred browser and type in localhost where you would normally type in a URL like google or what not.

It should display 2 links Apache & phpMyAdmin.

Click on the phpMyAdmin and it should load right up to it's log in page.  Use root as the user ID with no password and your in.

---

### Post by Medieval_Creations on 2007-01-27
> **phossal said:**
> 
I don't like phpadmin when I'm administrating mysql on my *own* computer. It's usually faster and easier to use the terminal.

Using the CLI is faster and I do use it when I can, but being a MySQL novice myself I sometimes cheat and do things through phpMyAdmin so I can see the generated code as a way of increasing my familiarity with MySQL commands.  :)

---

### Post by phossal on 2007-01-27
> **Medieval_Creations said:**
> Using the CLI is faster and I do use it when I can, but being a MySQL novice myself I sometimes cheat and do things through phpMyAdmin so I can see the generated code as a way of increasing my familiarity with MySQL commands.  :)

lol To each his own. I don't think there is anything *wrong* with phpMA. The command line isn't just for inputting the "basics" though. The terminal is fun because you can use source files to do everything you want, and you can combine that with scripts. That's powerful stuff.

---

