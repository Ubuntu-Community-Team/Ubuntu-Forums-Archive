---
title: "Cannot find device eth0"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Pieman15 on 2013-01-29
While doing a system upgrade my system froze. Somehow I lost both my wireless and ethernet network interfaces.
 
ifconfig -a only shows the lo interface
 
I added the following two lines to /etc/networking/interfaces as they were missing:
auto eth0
iface eth0 inet dhcp
 
I then ran sudo /etc/init.d/networking restart:
...restart is deprecated because it may not enable again some interfaces
...Cannot find device "eth0"
Failed to bring up eth0
 
Using Ubuntu 12.04. Thanks in advance for your help.
 
Solved: It seems like a system reboot after the edits to the networking interface were in order, the sudo /etc/init.d/networking restrart didn't do the trick. I had restarted this computer so many times this morning that I thought I already restarted after the edits, I guess not.

---

