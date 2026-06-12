---
title: "Change port 80 to non privileged"
date: 2009-03-06
forum: Programming Talk
---

### Post by cl333r on 2009-03-06
Hi folks,
Does anyone know how to do this?
Security is not an issue in my case.

---

### Post by dwhitney67 on 2009-03-06
Let's... umm, change it to 12345.

Seriously, what is it that you want to change?  The port number used by your apache web server?  If so, then I believe you should reference the config file for such.

---

### Post by cl333r on 2009-03-06
I want to make Ubuntu to allow ordinary users start services on port 80. Security aside, anyone knows how to do this?

---

### Post by dwhitney67 on 2009-03-06
Port 80 is generally known as the HTTP port, which Apache uses.  If you are not running an Apache web server, or you have it bound another port, then port 80 is available.

Since port 80 is below 1024, then it requires root-privileges to open/bind the port.

Thus if you have a server that requires the use of port 80, it will need to be started using root-privileges.  I do not believe there is a way around this.

Why port 80?  Why not choose 8080?

---

### Post by albandy on 2009-03-06
instead of doing this (I don't know how to do it) you can redirect the connection to port 80 to another port.

see the command redir
sudo apt-get install redir

---

### Post by cl333r on 2009-03-06
I ask to reply those who know how to make Linux allow an ordinary user start a service at port 80 (no redirects and alike).

---

### Post by eye208 on 2009-03-06
The only way to let ordinary users accept connections on port 80 is by providing an executable with the suid bit set (see [http://wiki.linuxquestions.org/wiki/Suid](http://wiki.linuxquestions.org/wiki/Suid)). If the user runs the executable, its process will be granted the privileges of the file owner, e.g. root. In this case the process can open a server socket listening on port 80. Once the socket handle has been obtained, the process can drop supervisor privileges for security reasons and continue using the socket.

---

