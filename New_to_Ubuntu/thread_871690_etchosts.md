---
title: "/etc/hosts"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-07-27
> Could not look up internet address for YOURCOMP. 
This will prevent Xfce from operating correctly. 
It may be possible to correct the problem by adding 
YOURCOMP to the file /etc/hosts on your system.

How do I fix this message.  It comes on my startup screen.  I googled it but the information I found was very confusing

---

### Post by Troll_the_Great on 2008-07-27
You can edit that file with the command:
```
sudo gedit /etc/hosts
```
Please post the content of the file first with no modification and we'll see what we can do :)
Cheers!

---

### Post by eightmillion on 2008-07-27
Run this command:

> sudo echo 127.0.1.1 `uname -n` >> /etc/hosts


---

### Post by AutumnPhoenix on 2008-07-27
this is basically what happpened for both commands:

> sudo: unable to resolve host USER
sudo: gedit: command not found


---

### Post by halitech on 2008-07-27
with Xubuntu, use mousepad instead of gedit (I think that is what it is called) or install gedit (from a terminal sudo apt-get install gedit )

---

### Post by eightmillion on 2008-07-27
I've seen this problem before. When your computer name isn't set up in the hosts file, you can't sudo. You could try booting into the recovery console and editing the file with nano but I suspect you might have to boot a live cd to fix it. Anyway, the line that you need to add to /etc/hosts is:
> 127.0.1.1     COMPUTERNAME
You'll have to replace COMPUTERNAME with the actual name of your computer.

---

