---
title: "mysql 5.1.25 - where to go...."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mspIggy on 2008-07-04
i have searched the Ubuntu >> Packages for mysql 5.1.25

i do not see it

where do i go for this ?

many thanks

---

### Post by jspolen on 2008-07-04
[http://dev.mysql.com/downloads/mysql/5.1.html#linux]("http://dev.mysql.com/downloads/mysql/5.1.html#linux")

This might work

---

### Post by mspIggy on 2008-07-04
many thanks

no nifty ubunto install from comand line package for this?

how in the world would i go about installing mysql from a tarball?

thank you

---

### Post by bhadotia on 2008-07-04
There should be a README or INSTALL text file in the archive file -find it . This will contain the information you need on  installation.
BTW, you can install MySQL 5.0 from the package manager if you don't want to manually install the software.

---

### Post by mspIggy on 2008-07-04
many thanks

i just installed the pgk for now - to see if i can even get the server up and running :)

i do need new mysql however, ultimatly

how long does it usually take to get these packages?

i see php 5.2.6 is there...

is there some reason no mysql?

many thanks

---

### Post by bhadotia on 2008-07-05
Well I have no idea about how long does it take for the package to included in the repos. But you can google for a .deb . If you can find it , you will easily be able to install it - Though even installing from the tar.gz shouldn't be that hard.

---

### Post by Tatty on 2008-07-05
MySQL 5.0.51 is in the repos.

It can be installed with ```
sudo apt-get install mysql-server
```

Unless there is a particular reason you need 5.1.25 then you should probably install the version from the repos, otherwise you will have to manually install any security updates which may come out.  Security patches in the repos will be pushed through to you.

**Edit:**
Ubuntu doesnt always have the latest versions of software in the repos, as often the latest versions may not be that stable.  Particularly with server apps which may be deployed in critical applications, care will be taken to ensure the included build is tried and tested to be stable.

---

