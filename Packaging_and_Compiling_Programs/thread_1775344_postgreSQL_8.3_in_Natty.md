---
title: "postgreSQL 8.3 in Natty?"
date: 2011-06-04
forum: Packaging and Compiling Programs
---

### Post by Sonja on 2011-06-04
I want to install postgreSQL 8.3 in Natty for Rails development, because that's what Heroku hosting uses. Natty seems to only offer 8.4. Is there a way to explicitly install 8.3? 

Thanks!

---

### Post by Harry Wood on 2011-07-28
Good question. Anyone know?

On the postgres site it recommends installing from packages: [http://www.postgresql.org/download/linux](http://www.postgresql.org/download/linux)   and it looks like the only way to get an 8.3 version is to compile from source. Even then I can't match the exact 8.3.8 version we have on our production server.

---

### Post by SevenMachines on 2011-07-28
Probably best to build and install a local version of postgresql but...

8.3 packages are here
[http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/)
and
[http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/)

8.3.8 is in universe for some reason
[http://archive.ubuntu.com/ubuntu/pool/universe/p/postgresql-8.3](http://archive.ubuntu.com/ubuntu/pool/universe/p/postgresql-8.3)

As I say, in my opinion probably best to build and install a local version for testing on if required. But those packages should work as far as dependencies and so on are concerned

[EDIT] Note that if 8.3.8 is no longer source downloadable from their website there's probably a reason, bug fixes, security fixes or whatever. Tends to be a good idea to have updated to the highest minor version for each major version for something like databases I'd say

---

