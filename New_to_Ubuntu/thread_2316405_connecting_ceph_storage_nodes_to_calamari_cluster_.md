---
title: "connecting ceph storage nodes to calamari cluster monitor 14.04"
date: 2016-03-07
forum: New to Ubuntu
---

### Post by doktor2 on 2016-03-07
[SIZE=2][FONT=arial]Hello,

I've installed three ceph storage nodes and i'm trying to monitor them , I found the calamari project for doing that.
(followed the instructions here: [http://bryanapperson.com/blog/compiling-calamari-ceph-ubuntu-14-04/](http://bryanapperson.com/blog/compiling-calamari-ceph-ubuntu-14-04/))

when i try to connect the nodes to calamari with: sudo ceph-deploy calamari connect ceph1
I get this error: [ceph_deploy][ERROR ] RuntimeError: no calamari-minion repo found

acording to this here: [http://calamari.readthedocs.org/en/latest/operations/minion_connect.html](http://calamari.readthedocs.org/en/latest/operations/minion_connect.html)  

I need to Create a ceph-deploy configuration file at ~/.cephdeploy.conf, containing a reference to a local repository in the following format, making appropriate substitutions as explained below:

[/FONT][/SIZE][FONT=arial][/FONT][SIZE=3][/SIZE][SIZE=2][FONT=arial]baseurl={minion_url}
gpgkey={minion_gpg_url}[/FONT][/SIZE][SIZE=2][FONT=arial]I've tried to use as suggested : [http://calamari/static/calamari-minions]("http://acme.mydomain.com/static/calamari-minions")
also: [http://calamari/static/calamari-minions/release.asc]("http://acme.mydomain.com/static/calamari-minions/release.asc")

i'm missing something about how to setup a local package repository.. 
please assist,
doktor[/FONT][/SIZE]

---

