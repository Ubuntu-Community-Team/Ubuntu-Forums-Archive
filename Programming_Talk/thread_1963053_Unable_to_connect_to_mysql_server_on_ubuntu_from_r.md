---
title: "Unable to connect to mysql server on ubuntu from remote computer"
date: 2012-04-21
forum: Programming Talk
---

### Post by Ed J on 2012-04-21
I'm trying to connect to a mysql database on my ubuntu box from a windows xp box on the same LAN. I've used GRANT in mysql to allow remote connections. I also ran
netstat -an | grep 3306
and verified that I am listening for tcp packets on port 3306, which mysql is configured to accept connections on.
  I am running a Java program that is just attempting to connect to the db. I am using the j connector and I get an error message that states "no packets were received from remote server" when running the java program.


Any suggestions?

BTW I am running ubuntu 11.10

---

### Post by Habitual on 2012-04-21
Firewall on ubuntu box?

---

### Post by Ed J on 2012-04-22
I gave up and shut everything down.
Turned it all back on and it works.
It could have been a configuration issue on either box.

I would say it was a waste of time but I learned something.

---

### Post by Habitual on 2012-04-22
> **Ed J said:**
> ...I would say it was a waste of time but I learned something.

Priceless :)

---

