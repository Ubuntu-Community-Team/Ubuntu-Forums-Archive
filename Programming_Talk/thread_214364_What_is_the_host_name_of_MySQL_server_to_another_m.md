---
title: "What is the host name of MySQL server to another machine on network?"
date: 2006-07-12
forum: Programming Talk
---

### Post by vayu on 2006-07-12
I use mysqlcc (MySQL Control Center) to access MySQL.  On the machine it's installed on I connect to it using host name 127.0.0.1. It works great. The IP address of that machine to the rest of the network is 10.0.0.20.  

I can't access MySQL from mysqlcc running on other machines on the network. I supply the same exact info (except for host which I give 10.0.0.20).

Giving 10.0.0.20 to a browser from other machines in the network pulls up the web page, and it also displays queries from that MySQL database.  (In other words no problem with the network, apache, php and php's ability to access MySQL)

Is there a permission or group setting I have to enable?  Or is the MySQL host name something other than the machine name? (The port is set to 3306 on both the local and remote mysqlcc programs)

---

### Post by ifokkema on 2006-07-12
Hi,

> **vayu said:**
> I use mysqlcc (MySQL Control Center) to access MySQL.  On the machine it's installed on I connect to it using host name 127.0.0.1.
Trivial information: 127.0.0.1 is not a hostname, but it's the local IP address (NOT the IP address your PC listens on from the network.

> **vayu said:**
> It works great. The IP address of that machine to the rest of the network is 10.0.0.20.  

I can't access MySQL from mysqlcc running on other machines on the network. I supply the same exact info (except for host which I give 10.0.0.20).
The problem is, that MySQL is not listening on the IP address your machine has on the network. This is a security feature.

Enable the MySQL server to listen on the network by editing /etc/mysql/my.cnf. There's a setting somewhere that you can change. It can be called skip-networking or bind-address. In the first case, you have to make sure it's disabled, in the latter you have to add 10.0.0.20. Don't forget to restart MySQL afterwards.

> **vayu said:**
> Giving 10.0.0.20 to a browser from other machines in the network pulls up the web page, and it also displays queries from that MySQL database.  (In other words no problem with the network, apache, php and php's ability to access MySQL)
When PHP is connecting to MySQL, it's using 127.0.0.1 or 'localhost' to connect, that's why that part works.

Have fun!

---

