---
title: "Coosing a database system"
date: 2008-06-16
forum: Programming Talk
---

### Post by AnthonyArde2 on 2008-06-16
Hi, i am creating a c++ application on ubuntu with netbeans and i require to know a few things before i begin, my application is going to be run on many computers which may be on a network or not, what i require is to ship a database with my application that is only accessable by the application on that computer. eg an access.mdb file would work for me. but this is ubuntu, i know that mysql is a database server and not just a database.

i basically require a way to access a db with my app and have it be able to ship with my application. any suggestions?

i would prefer to stay away from any scripting to generate a database, just looking for a way to access a db that is able to ship with my application.

thanks

Anthony

---

### Post by CptPicard on 2008-06-16
SQLite.

---

### Post by imneo on 2008-06-16
try using perl module for mysql

---

### Post by CptPicard on 2008-06-16
> **AnthonyArde2 said:**
> i am creating a **c++ application** on ubuntu

...

> **imneo said:**
> try using **perl** module for mysql


:confused:

---

### Post by aks44 on 2008-06-16
#-o

btw, +1 for SQLite

---

### Post by Munksgaard on 2008-06-16
I have yet to work with SQLite, but this tutorial seems like a nice place to start: [http://freshmeat.net/articles/view/1428/]("http://freshmeat.net/articles/view/1428/")

---

### Post by LaRoza on 2008-06-16
> **AnthonyArde2 said:**
> 
i basically require a way to access a db with my app and have it be able to ship with my application. any suggestions?


You want SQLite (haven't we heard this before :-))

It is used by many applications, including Firefox and Safari (not to mention many media players).

It is a small library that is very easy to use.

[http://www.sqlite.org/capi3.html](http://www.sqlite.org/capi3.html)

---

### Post by pmasiar on 2008-06-16
SQLite does not require running (and administering) of full-blown multiuser database server like MySQL does. It's a library, your programs uses it to fetch the data from file using SQL for access, but when calls ends, nothing runs anymore.

---

