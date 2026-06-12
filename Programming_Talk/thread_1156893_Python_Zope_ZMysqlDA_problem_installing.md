---
title: "Python Zope ZMysqlDA problem installing"
date: 2009-05-12
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-05-12
Hi Guys

I'm trying to setup the ZMySqlDA adapter for zope but I'm not seeing it show up in my ZMI

I installed the untar'ed  folder ZMysqlDA into the lib/python/Products folder and ran bin/runzope then I visit my ZMI but only the default Products are visible.

I then tried installing it into the Products folder in /usr/lib/zope2.10/lib/python/Products instead and started the server. Still no mysql adapter visible!

Anyone know whats going on?

Thanks in advance.

Mike

---

### Post by Mickeysofine1972 on 2009-05-12
Ok I did some snooping around it seems that Zope needs python 2.4 which is installed.

However, python2.4 doesnt have mysql installed as the package 'python-mysqldb' only installs support for 2.5 and 2.6!

Can anyone tell me how I can get the support for this installed for 2.4?

Mike

---

### Post by Mickeysofine1972 on 2009-05-12
Hi Guys

All sorted!

I got the old dapper drake python2.4-mysqldb deb and extracted it then placed the relevance files into the /usr/lib/python2.4/site-packages folder and restarted my zope server (2.10) and its fine so far 

Mike

---

