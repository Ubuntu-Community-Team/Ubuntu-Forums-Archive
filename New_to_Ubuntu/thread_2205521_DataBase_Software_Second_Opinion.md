---
title: "DataBase Software Second Opinion"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by Magnezone150 on 2014-02-14
Hi Everyone,

I'm Plan to have Ubuntu with KVM on my new Hp Proliant ML310e gen8 Server. 
But I also want it to be a Database for customer contacts and they're previous computer repair issues. 
Which Open Source Database Software do you think I should consider using?

---

### Post by tgalati4 on 2014-02-14
```
apt-cache search ticket
```

[http://bitnami.org/stacks/bug-tracking](http://bitnami.org/stacks/bug-tracking)

CRM might also apply:

[http://bitnami.org/stacks/crm](http://bitnami.org/stacks/crm)

---

### Post by SeijiSensei on 2014-02-14
You might start by looking into [ticket management systems]("http://blog.neweb.co/9-free-open-source-ticket-systems/") and let your choice of system determine your choice of database server.

[MySQL]("http://www.mysql.com/") is the most common choice though I personally use [PostgreSQL]("http://www.postgresql.org/").  I started with it in the days when MySQL was still proprietary and have used it for nearly two decades now.

---

### Post by Magnezone150 on 2014-03-18
Thank You Guys,
I Apologize for the very delayed response but I've decided to try OTRS and I like it so far.
Thanks Again!

---

### Post by slickymaster on 2014-03-18
> **SeijiSensei said:**
> You might start by looking into [ticket management systems]("http://blog.neweb.co/9-free-open-source-ticket-systems/") and let your choice of system determine your choice of database server.

[MySQL]("http://www.mysql.com/") is the most common choice though I personally use [PostgreSQL]("http://www.postgresql.org/").  I started with it in the days when MySQL was still proprietary and have used it for nearly two decades now.

A big +1 on SeijiSensei's post.

You could also consider [MariaDB]("https://mariadb.org/"), which is a community-developed fork of MySQL.

---

