---
title: "sudo apt-get remove --purge tv-maxe"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by marinoszak on 2012-06-13
i just typed this command: 
sudo apt-get remove --purge tv-maxe

and after that when i try to use apt-get, errors appears.
For example:
```
marinos@zak:~$ sudo apt-get install setserial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
setserial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up setserial (2.17-46) ...
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: /etc/rcS.d: no such directory
dpkg: error processing setserial (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lirc:
 lirc depends on setserial; however:
  Package setserial is not configured yet.
dpkg: error processing lirc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 setserial
 lirc

```

As i can see, i think that i removed some dependencies of apt-get package.

Thanks in advance.

---

### Post by JC Cheloven on 2012-06-13
setserial appears to be already installed, but misconfigured.

You can try ```
sudo dpkg-reconfigure setserial
```

If that fails, you could ```
sudo apt-get remove --purge setserial
``` and install it from scratch. Then care about lirc.

---

### Post by marinoszak on 2012-06-13
thank you.

---

### Post by daslinkard on 2012-06-14
Did this fix your issue?

---

### Post by zombifier25 on 2012-06-14
> **daslinkard said:**
> Did this fix your issue?

He does mark the thread as [SOLVED]

---

