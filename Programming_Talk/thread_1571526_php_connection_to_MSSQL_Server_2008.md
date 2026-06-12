---
title: "php connection to MSSQL Server 2008"
date: 2010-09-09
forum: Programming Talk
---

### Post by behzadsh on 2010-09-09
hi,

I'm a php programmer, Formerly I worked with mysql and I have no problem. In a new project I should work with MSSQL server DataBase.
My problem is that I'm programming in linux platform (ubuntu lucid), so I run windows 7 on vitualbox, Install SQL Server, Create a Host-Only Network from ubuntu to windows 7, but I couldn't connect to SQL SERVER through php. Now I don't know what should i do...

---

### Post by Some Penguin on 2010-09-09
A logical first step would be to determine whether MSSQL is actually receiving your connection requests.  Assuming that MS was not completely insane, they should have a log file containing such information.   If it doesn't see the request at all, then I'd want to test the networking with something reasonably known-good (i.e. set up something else that accepts network connections and see whether you simply don't have the networking link at all, or whether they're networked but maybe your client's connection configuration is simply borked).

---

### Post by behzadsh on 2010-09-09
Thanks, but I'm kinda newbie in networking can you explain more... [:oops: ]("http://ubuntuforums.org/member.php?u=963358")

---

### Post by behzadsh on 2010-09-10
I think problem is my connection to virtual machine,
I set up IIS on windows seven and try to access to it from ubuntu but connection time outed. I don't understand what's wrong, while I can ping the virtual machine IP4 address.

I have a little knowledge of networking, sorry if I do or say something wrong :oops:

---

### Post by Hellkeepa on 2010-09-11
HELLo!

Check that there are no firewalls blocking the connection attempts.

Happy codin'!

---

