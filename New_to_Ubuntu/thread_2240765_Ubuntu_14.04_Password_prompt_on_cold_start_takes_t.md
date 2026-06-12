---
title: "Ubuntu 14.04 Password prompt on cold start takes too long"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by victorw26 on 2014-08-22
After upgrading to Ubuntu 14.04, I began experiencing a logon problem from a cold start.  The password dialogue box is presented fairly quickly, but will not accept a password - I can not enter a password for around 1 minute.  During that time the mouse pointer is also frozen.  Is there any way that I can monitor what is going on during that time, or does anyone have a suggestion as to how to fix?  This problem did not exist before 14.04.  

It is only on a cold start or a re-start that this happens.  If I logoff, I can immediately enter the password for logging back on without a problem - no waiting involved.

---

### Post by ibjsb4 on 2014-08-22
Go to /var/boot.log

See if that has anything of use.

---

