---
title: "mysql on ubuntu"
date: 2007-06-29
forum: Programming Talk
---

### Post by glennyboiwpg on 2007-06-29
I installed mysql on ubuntu but the ubuntu box is suppose to be a server....

I need to be able to access the mysql server from my mac client... any ideas?

when I do a netstat port 3306 (mysql's port) is set to "listen"

does that mean its open?
 
I also edited a mysql file ( I can't remember which one at the moment, as i'm not infront of the server) and put the bind-address property to the ipaddress of the ubuntu box.  (I got the ipaddress from ifconfig)

any ideas?

Please respond. :(

---

### Post by tgm4883 on 2007-06-29
You want to comment out the line bind-address.  By setting that to the ipaddress of your server you are saying that only your server can connect to your mysql server.

---

