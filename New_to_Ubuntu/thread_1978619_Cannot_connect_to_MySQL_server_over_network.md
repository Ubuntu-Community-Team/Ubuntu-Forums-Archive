---
title: "Cannot connect to MySQL server over network"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by andperry on 2012-05-12
I have recently set up a computer on my home network using Ubuntu 12.04 Server and included the LAMP server in the installation. Everything seems basically fine with it except that I cannot connect to the MySQL server from another computer (running either Windows or Ubuntu Desktop). I've got copies of the same databases and the same PHP web pages on both the server and a desktop machine and the web pages run OK on both with the respective local MySQL server. On the desktop machine I then tried changing the MySQL server address from 'localhost' to the IP address of the Ubuntu server, and the web pages were outputting error messages saying that connection to the MySQL server could not be made. (The MySQL username and password are the same on all machines.)

I'm new to configuring Linux servers, but my instinctive feeling is that this is something fundamentally simple. Do I need to change a setting somewhere to allow the MySQL server to accept network connections?

Thanks.

---

### Post by cmont899 on 2012-05-12
Check /etc/my.cnf and make sure you are listening for outside connections. edit the line that starts with bind-address

change:
```
bind-address = 127.0.0.1
```
to:
```
#bind-address = 127.0.0.1
```

make sure mysql is running:
```
/etc/init.d/mysql status
```

if not, start it:
```
/etc/init.d/mysql start
```

check if the ubuntu firewall is running
```
sudo ufw status
```

if it is, allow mysql
```
sudo ufw allow mysql
```

---

### Post by andperry on 2012-05-13
Many thanks for the reply. I finally got it to work but needed to do something else as well.

Firstly I discovered along the way that one can either comment out the bind-address command or change it to the assigned static IP address of the server on the network (192.168.0.21 in my particular case) - as far as I can tell they have the same net effect.

Sorting out the bind address alone did not solve the problem (the Ubuntu firewall was disabled anyway), but having searched elsewhere online, I discovered that it was also necessary to set up the required access privileges on each database with the following type of SQL command:-

```
GRANT ALL ON `database`.* TO username@'%' IDENTIFIED BY 'password';
```All up and running OK now.

---

