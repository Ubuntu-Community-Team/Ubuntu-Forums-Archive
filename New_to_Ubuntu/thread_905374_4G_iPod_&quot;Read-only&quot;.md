---
title: "4G iPod &quot;Read-only&quot;"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-08-30
I have a 4G, Mac-formatted, 40 GB ipod. I want to use it with Amarok but it is said to be "read-only" I can't copy files manually, with amarok, or rhythmbox. 'gksudo nautilus' did not allow me to. 
Any ideas?

I think its the Mac formatting

---

### Post by linuxguymarshall on 2008-08-30
Anyone?

---

### Post by Tom--d on 2008-08-30
Right, 
As root
```
gksu nautilus
```
Go to computer on it. and right click the ipod and change the permissions to your username and read and write. Remember, as root.

---

### Post by linuxguymarshall on 2008-08-30
> **Tom--d said:**
> Right, 
As root
```
gksu nautilus
```
Go to computer on it. and right click the ipod and change the permissions to your username and read and write. Remember, as root.

It returned this 

> Sorry, couldn't change the owner of "disk": Error setting owner: Read-only file system

---

### Post by kc600 on 2008-12-01
Hi Marshall, 
Do you still have this problem? I opened a very similar thread at [http://ubuntuforums.org/showthread.php?p=6290399#post6290399](http://ubuntuforums.org/showthread.php?p=6290399#post6290399)

---

