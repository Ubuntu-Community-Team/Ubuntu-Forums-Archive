---
title: "Simplest way to connect to MySQL from Android?"
date: 2015-07-02
forum: Programming Talk
---

### Post by azzamite on 2015-07-02
If possible I'd like to connect directly to the MySQL database from an android app through a TCP socket...
but my research so far yielded that there is NO "connector" working for android.

What's the simplest way to communicate Android and MySQL (or PostgreSQL) ?

Seems like many people are using JSON, but I don't know what other alternatives are there, and also I
don't know how they do it in the server side (without PHP or HTML please!)

---

### Post by Dimarchi on 2015-07-04
Simply put, you can not avoid server side stuff. Not sure about RESTful here, though I doubt you can avoid server side there, either.

---

### Post by ofnuts on 2015-07-05
> **Dimarchi said:**
> Simply put, you can not avoid server side stuff. Not sure about RESTful here, though I doubt you can avoid server side there, either.

Not going through a sever would be a very bad design. This would also direct access to the DB by other apps, and also require your DB server to be directly facing the Internet...

---

