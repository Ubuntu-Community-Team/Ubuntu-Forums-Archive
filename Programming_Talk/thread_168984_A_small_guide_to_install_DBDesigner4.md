---
title: "A small guide to install DBDesigner4"
date: 2006-05-01
forum: Programming Talk
---

### Post by steparianwolf on 2006-05-01
Hi everybody!!:

A few days ago I posted a thread to ask for help to install DBDesigner4 in Ubuntu Breezy 5.10, but nobody answers to me :( 

In fact I installed DBDesigner4 succesfully, but  I couldn't connect to a MySQL Database, but finally I found how to solve to problem.

Problem 1
***"Unable to load libsqlmy.so"***

Search by Google, I found some people fix this problem by download the dbexpress library, I did it and solve the problem partialy, because with this library I can connect to Database but when I tried to Synchronize the E/R model, there was an error message: "List index out of bounds(7)"

Solve
Instead "LibraryName" option points to libsqlmy.so, put it to /path/to/libsqlmy23.so :-D 

Problem 2
***"Unable to load libmysqlclient.so"***

Solve
Instead "VendorLib" option points to libmysqlclient.so, put it to /path/to/libmysqlclient.so.10 :-D 

If you have problems to install or run DBDesigner after installation visit this how to [http://wiki.splitbrain.org/dbdesigner]("http://wiki.splitbrain.org/dbdesigner")

I hope this small guide helps everybody that have problems to connect with DBDesigner in ubuntu [like me]

By the way, sorry for my english but I'm from Mexico city and I don't speak english very well  :cool:

---

### Post by nife on 2006-05-16
Following this complains about xlibs is there any fix for this ?

---

### Post by yoyek on 2006-06-25
[QUOTE=nife]Following this complains about xlibs is there any fix for this ?[/QUOTE]

I have the same problem. I have installed xlibs-dev, but I still get "kylixlibs3-borqt depends on xlibs (>= 4.1.0); however: Package xlibs is not installed.", when I try to install "kylixlibs3-borqt_3.0-1_i386.deb"
Does anyone know how to fix it?

I'm using Ubuntu 6.06

---

### Post by yoyek on 2006-06-25
Ok, i have successfully installed xlibs from package: [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.1_all.deb).

And now I have problem with fonts - DBDesigner uses most ugliest fonts I ever seen in my life. How can I change this?

---

### Post by Dzo on 2006-08-24
I have exactly the same issue. Looking like its just the way the application is though, have a look at the screenshots on the website!

It's a shame because its seriously putting me off using it!

---

### Post by kno712 on 2006-09-17
> **Dzo said:**
> I have exactly the same issue. Looking like its just the way the application is though, have a look at the screenshots on the website!

It's a shame because its seriously putting me off using it!


Try installing the windows version with wine. Fonts are much better (IMO the website shows better fonts as well). Plus, you can connect to your databases without problems.

---

### Post by StefanRHRO on 2007-04-06
> Solve
Instead "LibraryName" option points to libsqlmy.so, put it to /path/to/libsqlmy23.so

Where can I find this library ( - package) on Dapper Drake?

Ok my fault, look in the Linuxlib directory... ;) But if I give the connection, an absolute path to the libmysqlclient.so.10.0.0 lib, I become an error too: Unable to Load: /blablabla/Linuxlib/libmysqlclient.so.10.0.0 

Can everybody help me. The path is 100% right!

---

### Post by steparianwolf on 2007-06-11
Hi:

You have to install libmysqlclient10 package from repos, in fiesty there is no longer the package in repos, but you can install from dapper repos. I have Ubuntu Feisty  and DBDesigner works fine

---

### Post by eracerbit on 2007-06-12
check out my comment here for a quick and easy working install method.

[http://ubuntuforums.org/showthread.php?t=125911#postcount2821196](http://ubuntuforums.org/showthread.php?t=125911#postcount2821196)

---

