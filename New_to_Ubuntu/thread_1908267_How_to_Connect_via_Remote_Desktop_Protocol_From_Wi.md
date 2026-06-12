---
title: "How to Connect via Remote Desktop Protocol From Windows Machines"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by tam3105 on 2012-01-13
Hi All,

I have configured Ubuntu 10.04 Lucid Lynx as domain and created users. Could any one help me,

How to Connect via Remote Desktop Protocol From Windows Machines? 

Also many users should be access this server at a time...

Thanks in advance...

---

### Post by stefangr1 on 2012-01-13
You can use, for example, the Real VNC client for that purpose. There's also an executable that doesn't require to be installed.

On the ubuntu side you have to set a password and allow logging in. Then you should be able to login from the windows machine by entering it's ip, leaving the username blank.

If you wan't to be able to login from the outside the steps are a little different. This because - for security reasons  - it may not be a very good idea to give the outside world access to the remote desktop server directly.

- You should install openssh server.
- Setup port forwarding of port 22 to your ubuntu system

Then use Putty (or any other ssh client) to connect to your ubuntu system and forward the port used by the remote desktop porticol (usually 5900). After that you can login with a VNC client by connecting to localhost.

NOTE: I just noticed that you wan't to connect many different users. The default desktop server, however, only lets you connect to the running session. To start new sessions you could install vnc server on the ubuntu side.

---

