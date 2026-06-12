---
title: "tarballs"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Vrekk on 2008-05-24
ok i want to install a plug in for pigion called gfire. well i got the .tar.gz off of the internet but and i was able to extract it with tar xzvf gfire-0.7.0.tar.gz and i dont know what to do from there. can anyone help?

---

### Post by Monicker on 2008-05-24
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by ramjet_1953 on 2008-05-24
This may be of help to you:

[http://frozenfox.freehostia.com/gfiregames.html](http://frozenfox.freehostia.com/gfiregames.html)

Regards,
Roger :cool:

---

### Post by Vrekk on 2008-05-24
nope no good, the frozen fox thing leed me to a page error and i followed the instrustions to install it and it said install failed.

---

### Post by Monicker on 2008-05-24
Please be more specific.

At what point did it fail?  What was the error message?

---

### Post by Vrekk on 2008-05-24
ok i know what the error was. i was trying to install a older verision of the software.  I went to the link Ramjet gave me and downloaded a newer one.  Thanks for the links guys :)

---

### Post by jong2x on 2008-05-25
i need help, i'm new to linux, and i can't install tarballs after i download it, i've tried different files to install please tell me what i'm doing wrong thanks.

james@james-laptop:~$ tar -xf /tmp/smilebubbles_lin.tgz
tar: /tmp/smilebubbles_lin.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
james@james-laptop:~$ tar -xf smilebubbles_lin.tar
tar: smilebubbles_lin.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
james@james-laptop:~$ tar -xf bshooter.tar
tar: bshooter.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: audacious-1.5.1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
james@james-laptop:~$ sudo alien -d xmms.rpm
[sudo] password for james: 
File "xmms.rpm" not found.
james@james-laptop:~$ 

i can't even use alien hehe... i use the commend sudo aptitude search, to search and install the files that i need but i can't install everything i need from there

help please... many thanks

---

