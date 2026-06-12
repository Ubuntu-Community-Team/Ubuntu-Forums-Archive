---
title: "terminal keyboard problem when SSHing in"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by spaceborne on 2008-07-04
Hi,

I'm accessing my Ubuntu Hardy server via SSH, using putty.  I'm running PuTTY on my Windows XP machine.

When I'm in root, i get all the normal keyboard functionality, eg.
* using the up key to get last command
* using the tab key to auto complete, etc.

I've created a new user. When I SSH into that user the terminal doesn't recognize those keys and writes ^[[A when I hit the up key, and puts in an ordinary tab when I hit tab.

Is this a .bashrc issue? Is it something with PuTTY?

Thanks.

---

### Post by Dr Small on 2008-07-04
I can't think of anything off the top of my head, but compare the .bashrc file or root and of the new user to see if there is any noticable difference.

---

### Post by bapoumba on 2008-07-05
Thread moved to Absolute Beginner Talk.

---

