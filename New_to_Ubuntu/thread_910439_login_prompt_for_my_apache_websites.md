---
title: "login prompt for my apache websites"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by moose4204l on 2008-09-04
I have an apace server. How do I create a login prompt so a person needs to enter the correct name and password or their name and password in order to view one of my directory sites. for instance [www.mydomain.com/my_sites_for_members....and](www.mydomain.com/my_sites_for_members....and) a prompt comes up with user name and password. I am looking for the basic security. After I have that running I will inquire about real security but I am looking to just block my brothers or friends from accessing the directory that I want only for my girlfriend or close friends so to speak...thanks

---

### Post by Cypher on 2008-09-04
The most basic way to put a password on a particular directory is to use Apache's [.htaccess]("http://httpd.apache.org/docs/1.3/howto/htaccess.html") file. This is the most basic authentication with a single username/password that will let people into a particular directory.

---

