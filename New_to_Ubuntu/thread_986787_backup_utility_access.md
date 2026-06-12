---
title: "backup utility access"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-18
i have just installed two backup utilities- partition imager and systemimager.  i was wondering how i can access both of these- is there a GUI to be launched for these programs and where can they be found?

thanks.

---

### Post by psusi on 2008-11-18
If it didn't appear on your menu, then no.  To see what files the package installed, run dpkg -L <package>.

Whatever it put in /bin, /usr/bin, /sbin, or /usr/sbin is going to be a command you can run.

---

