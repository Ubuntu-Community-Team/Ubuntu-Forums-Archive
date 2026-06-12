---
title: "* Starting domain name service... bind9 [fail]"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by sexytime on 2012-04-19
[LEFT]Please help
* Starting domain name service... bind9                                 [fail]
the domain keeps failing

> root@SwagTech1:/home/generalswag# apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  resolvconf
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/327 kB of archives.
After this operation, 1,085 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bind9.
(Reading database ... 140650 files and directories currently installed.)
Unpacking bind9 (from .../bind9_1%3a9.7.3.dfsg-1ubuntu4.1_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up bind9 (1:9.7.3.dfsg-1ubuntu4.1) ...
 * Starting domain name service... bind9                                 [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/LEFT]

---

### Post by richiesmithette on 2012-04-30
Hi,

I had the same problem. I resolved it by doing the following (as per this post: [http://forum.ubuntu-vn.org/viewtopic.php?f=56&t=1802](http://forum.ubuntu-vn.org/viewtopic.php?f=56&t=1802))

sudo apt-get purge bind9
sudo apt-get install bind9

Seems something was not right with one of the binaries started by /etc/init.d/bind9 - but was resolved only after a complete purge.

ie - reinstall! A bit drastic maybe, mine was on a staging server so I could take the risk. Obviously its a good idea to back up your existing zone/config files before doing this, just in case.

R

---

### Post by pot_roast on 2012-05-08
> **richiesmithette said:**
> Hi,

I had the same problem. I resolved it by doing the following (as per this post: [http://forum.ubuntu-vn.org/viewtopic.php?f=56&t=1802](http://forum.ubuntu-vn.org/viewtopic.php?f=56&t=1802))

sudo apt-get purge bind9
sudo apt-get install bind9

Seems something was not right with one of the binaries started by /etc/init.d/bind9 - but was resolved only after a complete purge.

ie - reinstall! A bit drastic maybe, mine was on a staging server so I could take the risk. Obviously its a good idea to back up your existing zone/config files before doing this, just in case.

R

May  8 22:33:26 heap named[25662]: starting BIND 9.8.1-P1 -u bind -t /var/lib/named
May  8 22:33:26 heap named[25662]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
May  8 22:33:26 heap named[25662]: adjusted limit on open files from 4096 to 1048576
May  8 22:33:26 heap named[25662]: found 2 CPUs, using 2 worker threads
May  8 22:33:26 heap named[25662]: using up to 4096 sockets
May  8 22:33:26 heap named[25662]: initializing DST: openssl failure
May  8 22:33:26 heap named[25662]: exiting (due to fatal error)

--
yes, same problems! Seems this is a long standing bug too that has now shipped with 12.04. THis is the second very serious bug that I have encountered!
I made a tar of my /etc/bind directory and tar skipped half the files in it. Now I need to re-make my config by hand. :-(

---

### Post by jgalvin2010 on 2012-07-18
Hi All Finally found a fix for this took a while:

Read this link just change the chroot directory to what ever you chrooted to :

[http://bridge.grumpy-troll.org/2012/05/pangolin-update.html](http://bridge.grumpy-troll.org/2012/05/pangolin-update.html)

Follow the instructions down to the letter and this should work fine it did for me anyway 

:P

---

