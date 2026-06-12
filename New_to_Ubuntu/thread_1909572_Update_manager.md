---
title: "Update manager"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-01-15
I got this message when updating. 

An error occurred

The following details are provided:

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/libg/libgadu/libgadu3_1.9.0-1~pidgin1.10.04_i386.deb](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/libg/libgadu/libgadu3_1.9.0-1~pidgin1.10.04_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/p/pidgin/libpurple-bin_2.9.0-1ubuntu0+pidgin2.10.04_all.deb](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/p/pidgin/libpurple-bin_2.9.0-1ubuntu0+pidgin2.10.04_all.deb)
  404  Not Found

What to do?..

---

### Post by grahammechanical on 2012-01-15
Uncheck those two lines in Software Sources and then the update will proceed. It seems that the link to location of the files for that program is broken.

This is what you should have in software Sources:

> deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main 

Check to see if there have been changes. This is where I got my information from:

[https://launchpad.net/~pidgin-developers/+archive/ppa/]("https://launchpad.net/~pidgin-developers/+archive/ppa/")

Use the drop down menu called **Display sources.list for** and select your version of Ubuntu. I have assumed 10.04. Are you still using 10.04?

Regards.

---

### Post by bluexrider on 2012-01-15
> **eduardo saxel said:**
> I got this message when updating. 

An error occurred

The following details are provided:

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/libg/libgadu/libgadu3_1.9.0-1~pidgin1.10.04_i386.deb]("http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/libg/libgadu/libgadu3_1.9.0-1%7Epidgin1.10.04_i386.deb")
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/p/pidgin/libpurple-bin_2.9.0-1ubuntu0+pidgin2.10.04_all.deb](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/pool/main/p/pidgin/libpurple-bin_2.9.0-1ubuntu0+pidgin2.10.04_all.deb)
  404  Not Found

What to do?..

Got the same here. Follow advice of grahammechanical. Solved

---

