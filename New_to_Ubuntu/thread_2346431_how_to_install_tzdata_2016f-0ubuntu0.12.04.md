---
title: "how to install tzdata 2016f-0ubuntu0.12.04"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by bantee on 2016-12-14
Running Ubuntu 12.04 (EOL is next April).  Been having some trouble with apt-get update working.  Narrowed down to this error:  [INDENT]  dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2016f-0ubuntu0.12.04); however:
  Version of tzdata on system is 2016j-0ubuntu0.12.04.

[/INDENT]
I have downloaded 2016f-0ubuntu0.12.04 from this site:  [https://launchpad.net/ubuntu/+source/tzdata/2016f-0ubuntu0.12.04](https://launchpad.net/ubuntu/+source/tzdata/2016f-0ubuntu0.12.04)

Downloaded 3 files, .xz, .gz, and .dsc   Having trouble with how to install these.

Thanks!

---

### Post by bantee on 2016-12-14
currently trying this:

copying all 3 files into 1 dir:
tzdata_2016f-0ubuntu0.12.04.debian.tar.xz  
tzdata_2016f.orig.tar.gz
tzdata_2016f-0ubuntu0.12.04.dsc

extracting the first 2:
tar -xJvf tzdata_2016f-0ubuntu0.12.04.debian.tar.xz
tar -xvzf tzdata_2016f.orig.tar.gz

Then trying the dsc file:
 sudo dpkg-source -x tzdata_2016f-0ubuntu0.12.04.dsc

Then it gives this message:

gpgv: Signature made Tue 05 Jul 2016 01:11:45 PM CDT using RSA key ID B1CDE58F
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./tzdata_2016f-0ubuntu0.12.04.dsc
dpkg-source: info: extracting tzdata in tzdata-2016f
dpkg-source: info: unpacking tzdata_2016f.orig.tar.gz
dpkg-source: info: unpacking tzdata_2016f-0ubuntu0.12.04.debian.tar.xz
dpkg-source: info: applying systemv.diff
dpkg-source: info: applying java.diff
--------------------------

Not sure if it's a problem, so I go ahead and edit the Makefile to have our correct timezone, then run sudo make install and get this error:

make: *** No rule to make target `tzselect.ksh', needed by `tzselect'.  Stop.

---

### Post by Impavidus on 2016-12-15
tzdata-java version 2016j-0ubuntu0.12.04 is available: [http://packages.ubuntu.com/precise-updates/libs/tzdata-java](http://packages.ubuntu.com/precise-updates/libs/tzdata-java)

Upgrading tzdata-java is normally better than trying to downgrade tzdata. Can you find out why your tzdata-java hasn't upgraded to 2016j?

---

