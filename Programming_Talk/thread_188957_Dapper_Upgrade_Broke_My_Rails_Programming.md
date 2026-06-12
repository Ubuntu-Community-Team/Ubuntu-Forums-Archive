---
title: "Dapper Upgrade Broke My Rails Programming"
date: 2006-06-04
forum: Programming Talk
---

### Post by moephan on 2006-06-04
Hello,

I upgraded my laptop to dapper yesterday, and in general the update went very very well. However, I am now having a problem with my ror applications. Every database call now returns an error like: 
```

mMysql::Error: Lost connection to MySQL server during query: SELECT * FROM moephan_users WHERE ( username = 'rick' ) LIMIT 1

```
Every database call does this. These statements work fine when I paste them directly into the mysql client.

I am running the version of rails installed from synaptic (1.1.2-1), and I tried reinstalling from synaptic.

I am far from a RoR expect, so any help and suggestions would be much appreciated. TIA.

Cheers, Rick

---

### Post by moephan on 2006-06-04
This turned out to be easy to fix. I found the anwer here:
[http://wiki.rubyonrails.com/rails/pages/Mysql+Connection+Problems/versions/12](http://wiki.rubyonrails.com/rails/pages/Mysql+Connection+Problems/versions/12)

The fix is simply to install this:
 apt-get install libmysql-ruby1.8

Cheers, Rick

---

