---
title: "Binary files damaged after attack on the server"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by viessenetwork on 2013-06-24
Hello,


a few days ago (June 19) a server that I manage has suffered an attack.
Analyzing the log I discovered that there were several attempts to access a web scanner called w00tw00t.at.ISC.SANS.DFind
I set the firewall to prevent further visits from this scanner.
The problem is that the server is compromised, however, in the sense that surely someone has gained access to the server and has damaged something.
In fact, everything worked except postfix.


If I tried to start it gives me error:


```
root@ns228442:~# /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix                                                                                                                              
/etc/init.d/postfix: line 39: /bin/sed: cannot execute binary file


root@ns228442:~# sh sed
/bin/sed: /bin/sed: cannot execute binary file


root@ns228442:~# sed
-bash: /bin/sed: cannot execute binary file


root@ns228442:~# sh -c sed
sh: /bin/sed: cannot execute binary file
```


I tried reinstalling postfix, but was deleted it and also was deleted some modules from plesk, plesk fact now will not start and the sites hosted on the server are not online.
If I try to re-install postfix or plesk always gives me error "can not execute binary file" on some commands, such as "sed" and "tar".


Then analyzing the bin folder I discovered that certainly a number of executables have been compromised, in fact they were modified date of the attack:




```
root@ns228442:/var/log# ls -l /bin | grep 'Jun 19'
-rwsr-sr-x 1 root root   20971 Jun 19 07:41 bleah
-rwxr-xr-x 3 root root   35272 Jun 19 07:41 bunzip2
-rwxr-xr-x 3 root root   35272 Jun 19 07:41 bzcat
-rwxr-xr-x 3 root root   35272 Jun 19 07:41 bzip2
-rwxr-xr-x 1 root root  113744 Jun 19 07:41 cp
-rwxr-xr-x 1 root root   14520 Jun 19 07:41 dbus-uuidgen
-rwxr-xr-x 4 root root   18832 Jun 19 07:41 dnsdomainname
-rwxr-xr-x 4 root root   18832 Jun 19 07:41 domainname
-rwxr-xr-x 1 root root   43424 Jun 19 07:41 echo
-rwsr-xr-x 1 root root   35480 Jun 19 07:41 fusermount
-rwxr-xr-x 1 root root   68264 Jun 19 07:41 gzip
-rwxr-xr-x 1 root root  153592 Jun 19 07:41 less
-rwxr-xr-x 1 root root   14600 Jun 19 07:41 lessecho
-rwxr-xr-x 1 root root   49088 Jun 19 07:41 login
-rwxr-xr-x 1 root root  101448 Jun 19 07:41 mv
-rwxr-xr-x 1 root root   39488 Jun 19 07:41 nc.openbsd
-rwxr-xr-x 1 root root   17427 Jun 19 07:41 netstat
-rwxr-xr-x 4 root root   18832 Jun 19 07:41 nisdomainname
-rwxr-xr-x 1 root root   39512 Jun 19 07:41 plymouth
-rwxr-xr-x 1 root root   23304 Jun 19 07:41 run-parts
-rwxr-xr-x 1 root root   73184 Jun 19 07:41 sed
-rwxr-xr-x 1 root root  348784 Jun 19 07:41 tar
-rwxr-xr-x 1 root root   39312 Jun 19 07:41 true
-rwxr-xr-x 1 root root   18808 Jun 19 07:41 ulockmgr_server
-rwsr-xr-x 1 root root   60776 Jun 19 07:41 umount
-rwxr-xr-x 1 root root  118128 Jun 19 07:41 vdir
-rwxr-xr-x 4 root root   18832 Jun 19 07:41 ypdomainname
```


All these executables listed do not work (give the error indicated).


```
root@ns228442:~# ldd /etc/init.d/postfix
    not a dynamic executable


root@ns228442:~# ldd /bin/sed
    not a dynamic executable


root@ns228442:~# file /bin/sed
/etc/magic, 4: Warning: using regular magic file `/usr/share/misc/magic'
/bin/sed: data
```


How do I restore these executables damaged?
I await help urgently!
Thank you!


P.S. here is more info that may be useful about the server:


```

root@ns228442:/bin# cat /proc/version
Linux version 2.6.38.2-xxxx-std-ipv6-64 (root@kernel-64.ovh.net) (gcc version 4.3.2 (Debian 4.3.2-1.1) ) #2 SMP Thu Aug 25 16:43:23 UTC 2011


root@ns228442:/bin# cat /etc/issue
Ubuntu 10.04.4 LTS \n \l


root@ns228442:/bin# cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

```

---

### Post by Cheesemill on 2013-06-24
Wipe the machine and re-install a fresh copy of Ubuntu Server before restoring all of your data from your last known good backup. It's the only way to be sure.

---

