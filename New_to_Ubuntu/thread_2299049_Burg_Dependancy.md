---
title: "Burg Dependancy"
date: 2015-10-15
forum: New to Ubuntu
---

### Post by Quarkrad on 2015-10-15
Running clean install of 14.04.  Try to install Burg Boot Loader with ** sudo apt-get install burg burg-themes**.  At the end of the install (via the terminal) I get:

     [B]dpkg: dependency problems prevent configuration of burg:
 burg depends on burg-pc (= 1.98+20100623-2.3); however:
  Package burg-pc is not configured yet.

dpkg: error processing package burg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 burg-pc
 burg
E: Sub-process /usr/bin/dpkg returned an error code (1)




                            dpkg: dependency problems prevent configuration of burg:
 burg depends on burg-pc (= 1.98+20100623-2.3); however:
  Package burg-pc is not configured yet.

dpkg: error processing package burg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 burg-pc
 burg
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

any help on what to do next appreciated.

---

### Post by yancek on 2015-10-15
Check their site below for instructions:

[http://howtoubuntu.org/how-to-make-your-dual-boot-better-with-burg](http://howtoubuntu.org/how-to-make-your-dual-boot-better-with-burg)

---

### Post by oldfred on 2015-10-15
Burg is getting old, and not maintained.

Note even in ppa last update is 2011-10-15
[https://launchpad.net/~n-muench/+archive/ubuntu/ppa](https://launchpad.net/~n-muench/+archive/ubuntu/ppa)

---

