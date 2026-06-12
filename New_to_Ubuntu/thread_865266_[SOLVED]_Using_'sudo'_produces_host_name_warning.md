---
title: "[SOLVED] Using 'sudo' produces host name warning"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by dwhitney67 on 2008-07-20
Everytime I use 'sudo' to run a root-privileged command, 'sudo' allows me to continue with my request, however displays a warning message of:
```
sudo: unable to resolve host bluediamond
```
Btw, bluediamond is my system's hostname (in /etc/hostname).

What is causing this warning to be displayed, and more importantly, what do I need to do to correct it??

Does this have anything to do with the contents of my system's /etc/hosts file?  That was the last thing I remember tinkering with.  The /etc/hosts file looks like:
```
127.0.0.1     localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
I used to have an entry, if I recall correctly, with an IP of 127.0.1.1, but I removed that.  Does anyone have something similar in their /etc/hosts file?

---

### Post by TSS on 2008-07-20
I believe putting bluediamond on a 127.0.1.1 line in your hosts file should fix this.

---

### Post by Elfy on 2008-07-20
This is mine, kevin-desktop is my hostname

> 127.0.0.1	localhost
127.0.1.1	kevin-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 hosts needs to match hostname afaik

bit of a pain to fix without using sudo :) try doing it in recovery if necessary

---

### Post by dwhitney67 on 2008-07-20
Thanks TSS and forestpixie... that was it!  I updated the /etc/hosts file and the next time I ran sudo the warning was no longer displayed!

---

