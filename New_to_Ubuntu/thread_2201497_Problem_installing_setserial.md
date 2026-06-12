---
title: "Problem installing setserial"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by eawy on 2014-01-24
Hi you all,

I am just starting with this, and I have tried to solve this by myself, but I am allways getting the same message:



root@raspbmc:/usr# apt-get install setserial
Reading package lists... Done
Building dependency tree
Reading state information... Done
setserial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up setserial (2.17-47) ...
update-rc.d: warning:  stop runlevel arguments (0 6) do not match etc-setserial Default-Stop values (0 1 6)
insserv: Can not stat : No such file or directory
insserv: Can not stat S17rsync: No such file or directory
insserv: warning: script 'S17rsync' missing LSB tags and overrides
insserv: Can not stat : No such file or directory
insserv: Can not stat S17rsync: No such file or directory
insserv: Can not stat : No such file or directory
insserv: Can not stat S17rsync: No such file or directory
insserv: Can not stat : No such file or directory
insserv: Can not stat S17rsync: No such file or directory
insserv: Service checkfs has to be enabled to start service etc-setserial
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing setserial (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 setserial
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@raspbmc:/usr#



Thanks you all!

---

### Post by eawy on 2014-01-25
Anyone?

---

### Post by Iowan on 2014-01-25
Is the machine name a coincidence, or is this a [raspbmc]("http://www.raspbmc.com/") install?

---

