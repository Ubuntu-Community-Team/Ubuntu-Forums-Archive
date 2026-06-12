---
title: "simpile C FTP server"
date: 2013-02-06
forum: Programming Talk
---

### Post by conradin on 2013-02-06
Hi All, 
I am looking for the source code of a simple ftp server in written in C, CPP, or maybe python. User accounts and passwords is the top of functionality I would like to look at. 

Theres alot of code out there, anyone have some good recommendations?
Simple is best.

Something like this:
[http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)
but with an ability to have a user / password.
Ill try to figure it out on my own, but I would preffer to have some good stable code to work with.

---

### Post by Bachstelze on 2013-02-06
The simplest ftpd I know of is the one that is built into most BSD OSes nowadays. However, since it is built into the OS and not a standalone program, I don't know to which extent the code is self-sufficient. There is also this: [http://packages.ubuntu.com/quantal/ftpd](http://packages.ubuntu.com/quantal/ftpd)

Also, do you really need FTP, or just something to transfer files with a username/password? FTP is a lot more than that.

---

