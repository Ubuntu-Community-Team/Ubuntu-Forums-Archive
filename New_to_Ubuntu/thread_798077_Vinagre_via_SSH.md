---
title: "Vinagre via SSH?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ptn107 on 2008-05-17
In the days of Ubuntu 7.10 it was easy to use 'vncviewer -via' to remote desktop over SSH.  With Hardy, however, vncviewer is not installed by default.

Is there a way to use remote desktop over SSH using the new vinagre vnc program that is installed by default in Hardy?

---

### Post by andrewkk on 2008-05-18
I was just wondering this myself. SSH tunneling is something that I'd expect to see built in to a client like Vinagre, but it doesn't look like it has that capability (yet).

I'm having trouble accessing [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) right now so I don't know if there's been any push yet to have this implemented. There were a few comments talking about it on [an old blog post]("http://www.bani.com.br/2007/09/14/new-project-vinagre-vnc-client/"), and [Ubuntu brainstorm]("http://brainstorm.ubuntu.com/") might also be worth looking at.

For now, I've just been getting by with
[LIST=1]
[*][FONT="Courier New"]$ ssh -L 5900:127.0.0.1:5900 hostaddress[/FONT]
[*]Use Vinagre to connect to host [FONT="Courier New"]127.0.0.1[/FONT]
[/LIST]

---

### Post by bgs100 on 2008-12-03
bump so this post will continue, cause I have the same problem

---

### Post by skliarie on 2009-07-04
There is bug report (wishlist) on the issue:
[https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/273298]("https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/273298")

---

### Post by karlstad on 2010-04-06
This seems to have been included in the new version of Vinagre (2.30.0) which is included in Lucid.

---

