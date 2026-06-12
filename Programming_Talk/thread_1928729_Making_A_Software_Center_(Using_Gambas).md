---
title: "Making A Software Center (Using Gambas)"
date: 2012-02-20
forum: Programming Talk
---

### Post by ryanrio95 on 2012-02-20
Is there a way to request package information, search for packages etc. using Gambas.
I'am learning Bash and Gambas by the way. So is their someone that could help me?

I tried a few things with the Shell command in Gambas. But i want to have a MySQL database with packages. And that the packages are sorted by downloads. And when a package is clicked to install. It will do +1 in mysql under downloads. MySQL isn't the problem. But getting information about packages. And searching packages.

Regards, Ryan.

---

### Post by nebukadnezzar on 2012-02-21
There are currently many things wrong about what you are trying to do. But allow me to boil it down a little.

> 
Is there a way to request package information, search for packages etc.


[Yes.](http://packages.ubuntu.com/oneiric/libapt-pkg-dev)

> using Gambas.
No. Not without a binding, that is.

> But i want to have a MySQL database with packages

APT is already using a database. You achieve nothing by storing them *again* in a *different* database.

> And when a package is clicked to install.

That sentence doesn't make much sense to me.

> It will do +1 in mysql under downloads

Neither does this one.

> But getting information about packages. And searching packages.


Both possible with libapt.

---

### Post by ryanrio95 on 2012-02-21
Okay, is there a way to get output of command line with gambas?

I know how to run an command:
```
Shell "gedit"
```
for example.

Regards

---

