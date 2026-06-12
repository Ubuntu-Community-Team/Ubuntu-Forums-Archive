---
title: "How To Install VMware Server On Ubuntu 6.06 LTS (Dapper Drake)"
date: 2006-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by lex1 on 2006-07-28
**How To Install VMware Server On Ubuntu 6.06 LTS (Dapper Drake)**

here is an excellent howto

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

lex1

---

### Post by supafly_stud on 2006-07-29
major props for this...

note:
this howto worked for me and i followed it word for word

thanks alot

---

### Post by supafly_stud on 2006-07-30
another quick note:

make you do this before you start this guide>>

```
uname -r
```
^this will give you a number (eg. 2.6.15-26-386)



then do this command, putting the number from above in the noted area>>

```
sudo apt-get install linux-headers-"insert number here" build-essential xinetd
```

THEN continue on with this foolproof install!

---

### Post by hambone088 on 2006-08-09
I followed the instructions word for word along with the quick note and everything seemed to install just fine.  The problem is that when I go to start vmware-server-console I get the following three errors...

/usr/bin/vmware-server-console: line 85: /etc/vmware-server-console/locations: No such file or directory
/usr/bin/vmware-server-console: line 177: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware-server-console: line 177: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory

Any help is appreciated.

thanks.

---

### Post by emiri-2.0 on 2007-09-05
to install vmware-console from rpm package:

Transform it to .deb with alien tool

```

emiri@emiripc:~/Desktop$ sudo alien --scripts VMware-server-console-1.0.3-44356.i386.rpm

```

Install it

```

emiri@emiripc:~/Desktop$ sudo dpkg -i vmware-server-console_1.0.3-44357_i386.deb 

```

Execute first time

```

emiri@emiripc:~/Desktop$ vmware-server-console 
vmware-server-console is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config-server-console.pl.

```

Execute refered perl script

```

emiri@emiripc:~/Desktop$ sudo /usr/bin/vmware-config-server-console.pl 

```

And you can execute vmware-server-console program without problems

++
e.

---

