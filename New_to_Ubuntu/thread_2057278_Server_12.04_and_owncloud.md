---
title: "Server 12.04 and owncloud"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by hkl@hkl.no on 2012-09-13
Hello anyone

I just installed owncloud on an ubuntu 12.04 server (sudo apt-get install owncloud)
Everything seemed fine, i can access owncloud on [http://localhost/owncload](http://localhost/owncload)
When i try to connect a Windows client I get the follwing error msg:

Trying to connect to ownCloud at [https://192.168.1.74/owncloud](https://192.168.1.74/owncloud)...
Failed to connect to ownCloud!
Error: Connection refused
An ownCloud connection could not be established. Please check again.

Any ideas?

hkl

---

### Post by androssofer on 2012-09-13
> **hkl@hkl.no said:**
> Hello anyone

I just installed owncloud on an ubuntu 12.04 server (sudo apt-get install owncloud)
Everything seemed fine, i can access owncloud on [http://localhost/owncload](http://localhost/owncload)
When i try to connect a Windows client I get the follwing error msg:

Trying to connect to ownCloud at [https://192.168.1.74/owncloud](https://192.168.1.74/owncloud)...
Failed to connect to ownCloud!
Error: Connection refused
An ownCloud connection could not be established. Please check again.

Any ideas?

hkl

your first link uses http:

> [http://localhost/owncload](http://localhost/owncload)

however the second is https (ie: using ssl):

> [https://192.168.1.74/owncloud](https://192.168.1.74/owncloud)

is this a typo?

if not it could be that owncloud is only listening for http..

and thus the https (ssl) connection will fail.

---

### Post by aadam12 on 2013-01-02
Continuing on that thought...  How do I force Owncloud to use https? I am running Ubuntu 12.10 Server 64-bit. 

I too installed owncloud by doing sudo apt-get install owncloud.
I can access my owncloud inside my network from any machine by going to [http://192.168.1.100/owncloud](http://192.168.1.100/owncloud)

Before I expose my owncloud to the outside world by portforwarding on my router, I would like to make sure it is using https.

---

### Post by eenofonn on 2013-01-15
> **aadam12 said:**
> Continuing on that thought...  How do I force Owncloud to use https? I am running Ubuntu 12.10 Server 64-bit. 

I too installed owncloud by doing sudo apt-get install owncloud.
I can access my owncloud inside my network from any machine by going to [http://192.168.1.100/owncloud](http://192.168.1.100/owncloud)

Before I expose my owncloud to the outside world by portforwarding on my router, I would like to make sure it is using https.

Couldn't you just forward 443 or whatever port the https is running on?

---

