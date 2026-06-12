---
title: "Web development, quanta and xampp"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by tradet on 2008-09-17
I'm a beginning web developer and just recently I got my very own site complete with a domain name and everything! :) I wanna test quanta as my wysiwyg tool but I have some problems. I got xampp installed and I can get it to start and stop just fine but the mysql part is very confusing. 

Now mind you I can use my mysql server I got from the web hosting company but I dunno what real developers do... are they using that or do they have their own home server for testing? And if so they have to manually change the code every time they upload the site which sounds very troublesome to me.

A bigger problem is that I can't copy my site, from my vista partition, in '/media/disk/xampp/htdocs' to '/opt/lampp/htdocs' as I don't have permission to.

Also I can't preview the standard index.html file from htdocs in quanta (f6).

When I try to create a new project, at the location of htdocs I get the error 'cannot open file /opt/lampp/htdocs/name.webprj'.

Glad for some insight to this.

---

### Post by MegaJim on 2008-09-17
This wiki page gives some insight into how ubuntu deals with ntfs partitions:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Ryadt on 2008-09-17
To change the permission of htdocs. Do
```
gksudo nautilus
```
Then change the permission of the htdocs folder in there.

---

