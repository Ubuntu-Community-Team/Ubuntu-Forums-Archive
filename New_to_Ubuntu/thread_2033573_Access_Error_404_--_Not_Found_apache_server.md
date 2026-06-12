---
title: "Access Error: 404 -- Not Found apache server"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by vikka on 2012-07-26
This error just occurred out of the blue, i had not done anything just came home from work and the server didn't seem to respond when i tried to access any webcontent. 

I did a simple restart of the apache2 service and it worked again.
The error message i got from all webdirectories was:
Access Error: 404 -- Not Found apache server

Any idea?

---

### Post by FatFrog on 2012-07-26
Have you gone through the logs to find any errors?

---

### Post by richpri on 2012-07-26
Run in terminal

more /var/log/apache2/error.log

And post any significant messages

---

### Post by vikka on 2012-07-26
> **FatFrog said:**
> Have you gone through the logs to find any errors?

Last stuff to occur was this:
I'll be keeping a close look at the log and events to see if it occurs again.
> 

sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
sh: 1: /usr/sbin/sendmail: not found
[Thu Jul 26 19:03:16 2012] [notice] caught SIGTERM, shutting down
[Thu Jul 26 19:03:17 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jul 26 19:05:54 2012] [notice] caught SIGTERM, shutting down
[Thu Jul 26 19:07:12 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations



---

