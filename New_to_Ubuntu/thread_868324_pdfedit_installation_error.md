---
title: "pdfedit installation error"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by jmendez2 on 2008-07-23
Hi all,

I am having a difficult time installing pdfedit on Dapper.
I followed the instructions at [https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)
and used GDebi to install it, but I get the following error:
Error: Dependency is not satisfiable: libc6

I also tried Method 2 and got the following error:
pdfedit: /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.4' not found (required by pdfedit)

I used synaptic to reinstall the libc package but still get the same errors.

Any suggestions are greatly appreciated!

---

### Post by stevoo on 2008-07-23
Perhaps you are missing the libc6....
open a terminal and type in there 
sudo apt-get install libc6
Enter password and try again

---

### Post by jmendez2 on 2008-07-23
This is what I get:

jmendez@jmendez-laptop:~$ sudo apt-get install libc6
Password:
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
jmendez@jmendez-laptop:~$

I have it updated :(

---

### Post by stevoo on 2008-07-23
[http://www.getdeb.net/download/2390/0](http://www.getdeb.net/download/2390/0)

donwload this and run it ... see if all dependencies are met

---

### Post by moore.bryan on 2008-07-23
often, installing complains when the dev aspect of a certain program is not installed. for example, if it claims libc6 isn't up to snuff and you have it installed, try installing libc6-dev or similar; usually, that's enough to make it go.

---

