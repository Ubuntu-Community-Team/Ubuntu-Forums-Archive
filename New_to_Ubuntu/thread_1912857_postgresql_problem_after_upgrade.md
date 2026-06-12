---
title: "postgresql problem after upgrade"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by agenjtoa on 2012-01-21
Hi,

I'm very new to Ubuntu and even moreso with the terminal commands etc. I'm learning my way through (googlin'). 

I have been trying to install an application to that requires the use of postgresql. I was making headway following the guide until I decided to upgrade from Ubuntu 11.04 to 11.10 when I believe there was installation of postgresql 9.1 as well. 

After doing this I was unable to create a database I get the below error

Is the server running locally and accepting connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

I've googled this and it said to ensure postgresql was running, checked and it was. 

After various things, it still wasn't working so I decided to remove postgresql 8.4 and 9.1 (as I had entries for both in /etc/postgresql). Used the pg_dropcluster following another site reference

now I have no entires in /etc/postgresql (before I had both 8.4 and 9.1

Even though I re-installed using apt-get, these don't appear anymore. 

Any help would be great!

agenj toa

---

### Post by agenjtoa on 2012-01-26
anyone with postgresql knowledge? Otherwise I may need to reinstall the whole O/S as I don't know how else to restore the application/database.

---

### Post by GraeW on 2012-01-27
I would think the removal of all versions and reinstallation of one version (latest?) postgresql would have helped your situation; I have only a passing experience with it and never got very far. Bumping for you again - hope someone else can pop in with an answer!

---

