---
title: "Upgrading Request Tracker 3.6.4 to 3.6.6"
date: 2008-01-30
forum: Programming Talk
---

### Post by ewanchic on 2008-01-30
I am currently using Request Tracker 3.6(.4) which is a nice automatic install from apt manager:
> apt-get install request-tracker3.6 rt3.6-apache2 rt3.6-clients libdbd-pg-perl

Well, last week Request Tracker updated their version to 3.6.6. YEAH!
[http://bestpractical.typepad.com/worst_impractical/2008/01/rt-366-now-avai.html](http://bestpractical.typepad.com/worst_impractical/2008/01/rt-366-now-avai.html)

And I would like to upgrade. Upgrade manually and perhaps help upgrade the package as well. I'm a little crunched for time, and I was hopping someone could help me with the configure options I would need to execute: [http://wiki.bestpractical.com/view/ManualInstallation](http://wiki.bestpractical.com/view/ManualInstallation)

For example:
>   ./configure --prefix=/etc/request-tracker3.6 --exec-prefix=/usr/local/share/request-tracker2.6
etc.

Thanks :)

---

### Post by ewanchic on 2008-02-04
I'm still researching away. So far, this is my best guess...

> 
./configure --with-db-type=Pg --with-db-database=rtdb --with-db-rt-user=rtuser --with-db-rt-password=wibble \
 --prefix=/usr/local/share/request-tracker3.6 --exec-prefix=/usr/share/request-tracker3.6 --bindir=/usr/bin \
 --sbindir=/usr/sbin  --includedir=/usr/include --infodir=/usr/share/info --mandir=/var/cache/man


...but i'd like to test this. Is there a way I could see where all of the files get placed, like in a -verbose output, but the files themselves do not actual get installed.

I've gotten some help from the config.status output and looking and debian's current package, but I'm just not comfortable with actually installing this yet. I think I get some of it right and others I will need to correct. 

If anybody could suggest debugging ideas, that would be great!

---

### Post by ewanchic on 2008-02-05
I'm assuming this thread has been forgotten. I was really hoping the person who put this debian package together would help out, but who knows.

During my research, I found a lot of files scattered throughout, and I was really hopeful that I could get this mapping accomplished. Unfortunately, I was not sure if my configure script would work properly, and since I am in a time crounch, I'm not will to try it unless I can execute a test tun first. 

So, for myself and my coworker, we've decided not to pursue this issue anymore.

---

### Post by ewanchic on 2008-02-07
*bump*

While talking to a mod on IRC looking for advice on moving this thread to another topic, he/she suggested that I *bump*. I'm not sure what that means. :)

---

### Post by adelhier on 2008-02-21
I just upgrade RT from 3.6.4 to 3.6.6 and there where some packages that were missing from the gusty package tree that i had to ether use the hardy universal sources and hand compile one tar ball by hand as it dose not have a package at all.

i had to use hardy to install Package: libdbix-searchbuilder-perl (1.50-1) [universe] gusty only had 1.46 and rt 3.6.6 needs 1.50

Then it was looking for CSS::Sqiush witch i had to install from a tar ball but it need the package libtest-longstring-perl from the gusty universe package tree.

So to get the hardy package i added it package source and run the install then removed it from the source list.

on the ./configure i only did the prefix and database password as i am using mysql.  You may want to stay with mysql as the base rt package as it as the install dependent in the source tree.  After i get it all squared away i post up if it all worked and if i did have some problems the work arounds i used.

Andy

---

