---
title: "file permissions"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by einfinger on 2008-08-23
im having problems with getting permissions to set sharing on any given folder in ubuntu. 
i right click and select share folder but when nautilus asks to set additional properties i get an error message saying that it couldnt set sharing because of permission restrictions.
what am i doing wrong ?

---

### Post by cmnorton on 2008-08-23
You might not own the folder in question, which is why you are getting the error. 

Answering this question is not as simple as giving you a bunch of commands. You would need to determine who owns the directory, whether or not you are in the same group as the owner, and then, as sudo, changing permissions and/or the owner.

---

