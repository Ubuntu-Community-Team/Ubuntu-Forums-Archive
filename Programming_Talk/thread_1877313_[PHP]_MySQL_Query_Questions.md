---
title: "[PHP] MySQL Query Questions"
date: 2011-11-07
forum: Programming Talk
---

### Post by hantechbl on 2011-11-07
I am writing a script that will be accepting remote input, however I only want the script to accept input from only specified IP addresses, how would I go about checking a Database to see if a column in a certain table(IP address) Matches the that the client has?  Basically just a IF-IP-exists, then proceed, else exit type thing.

---

### Post by fdrake on 2011-11-07
> **hantechbl said:**
> I am writing a script that will be accepting remote input, however I only want the script to accept input from only specified IP addresses, how would I go about checking a Database to see if a column in a certain table(IP address) Matches the that the client has?  Basically just a IF-IP-exists, then proceed, else exit type thing.

```
man inet
less /etc/hosts.allow
```

---

### Post by 1clue on 2011-11-07
I know only slightly more about it than fdrake does.

First you need to convince mysqld that it can accept connections from something other than localhost.

Although, maybe you could get around it by enclosing your sql query in ssh.


Something like:

ssh <remote ip> mysql <connect info> "select ..."

which would get around the localhost problem without sacrificing much on security and completely avoid reconfiguring mysql.

---

### Post by hantechbl on 2011-11-07
I made a mistake in wording the question:
The PHP script will handle the DB connections, the PHP script must check if the IP is present in a certain column of a table, if it is present then the script will continue, if the client's IP isn't in the database, then it will return a error.

---

### Post by 1clue on 2011-11-08
select 1 from table where ip = 'value'

Use whatever PHP command returns an int value or scalar value.  In hibernate there's a queryForInt.

---

### Post by hiteshhk on 2011-11-09
> **1clue said:**
> select 1 from table where ip = 'value'

Use whatever PHP command returns an int value or scalar value.  In hibernate there's a queryForInt.

appreciated....gud answer

---

