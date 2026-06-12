---
title: "Jetty 6.1.22 on Ubuntu 12.04 LTS?"
date: 2012-11-28
forum: Repositories &amp; Backports
---

### Post by Ex_Stuntman on 2012-11-28
I'm running into problems with a java application that stopped working when I upgraded my 10.04 LTS server to 12.04 LTS..  my guess is that something in the Jetty upgrade from 6.1.22 to 6.1.24 is causing problems with my application.  I'd like to roll back Jetty to 6.1.22 and see if things work out again.

I'm a linux noobie, so be kind..  I'm learning, but it is a pretty steep curve!

Thanks!

---

### Post by Jason80513 on 2012-12-05
Check out your Java versions. Make sure, since this is an upgrade and you had things that depend on Java installed, that you don't have some settings that are pointing to a Java runtime that doesn't exist anymore.

---

