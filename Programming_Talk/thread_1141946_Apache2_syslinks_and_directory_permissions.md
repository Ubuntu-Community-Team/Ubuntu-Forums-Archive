---
title: "Apache2 syslinks and directory permissions"
date: 2009-04-28
forum: Programming Talk
---

### Post by king vash on 2009-04-28
I am running 
ubuntu 9.04
Apache/2.2.11 
mod_python/3.3.1 
Python/2.6.2

I am trying to be able to link to /home/king/Pictures from my server (preferable via a url such as [www.servername.com/Pictures](www.servername.com/Pictures))

I tried followsyslinks but was unable to get it to work
I tried adding this to my http.conf
<Directory ~ "^/home/king/Pictures/.*">
	Order Deny,Allow
	Allow from all
</Directory>

I tried creating a group and adding www-data, my user... and chowning the folder to that group.
I tried adding other read \ execute
I was unable to ever read from the file over apache.


I would also like to be able to read and execute from \home\king\scripts\


I have been working on this for several days and am stuck against a wall any help would be appreciatede

---

