---
title: "What port numbers does GNOME use (and the system in general)"
date: 2008-05-10
forum: Programming Talk
---

### Post by keeler1 on 2008-05-10
I have had to do a project for a class of mine in which we have to modify kernel 2.6.24 (using Ubuntu 6.06 LTS)  We had to implement a kernel firewall of sorts where certain files are barred access no matter the file permissions and access to inet sockets are granted access if they have been specified.  

I have gotten all of this to happen, but GNOME seems to have issues with my kernel blocking inet ports.  For testing purposes I would like to add whatever ports GNOME needs to my list of ports that are granted access with inet sockets.  However I can not seem to find this information on google.

So,  does anyone know what ports GNOME uses.

Also, what are some other ports that a general system would use regularly.

---

### Post by slavik on 2008-05-11
80, 23, 631 are the 3 important ones that come to mind.

---

### Post by keeler1 on 2008-05-11
Does anyone else know of any others.  When I disable most ports except the few mentioned by the previous post.  The GNOME shutdown does not work.  I assume that it is using some ports and sockets.

If anyone knows those specifically that would be great.

---

### Post by stroyan on 2008-05-11
You can see what ports are currently in use by running 'netstat -tan'.
You can look at a very long list of potential port use by reading /etc/services.

---

