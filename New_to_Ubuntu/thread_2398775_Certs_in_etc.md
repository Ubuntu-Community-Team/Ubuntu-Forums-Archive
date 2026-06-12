---
title: "Certs in /etc"
date: 2018-08-17
forum: New to Ubuntu
---

### Post by mborl on 2018-08-17
Can someone explain the certificates in the /etc folder? I'm new to Ubuntu and cyber security. Does this directory hold my private keys for asymmetric encryption?

---

### Post by TheFu on 2018-08-17
Directories  below /etc/ hold server keys and CA CRT information.  Some are for public CAs, some are for the local machine and some can be installed for local company CAs.

In all Unix environments, individual settings are stored inside the users' HOME. Server settings are generally installed under /etc/, there are exceptions.  An admin can override almost anything, though most don't.

If you want to understand what goes where, there is a **file system hierarchy standard** that Linux distros and many Unix distros follow. google finds it easily.

---

### Post by mborl on 2018-08-19
Thanks. I know some wifi networks require you to go find a certificate in etc/ssl/certs

---

### Post by TheFu on 2018-08-19
> **mborl said:**
> Thanks. I know some wifi networks require you to go find a certificate in etc/ssl/certs

Those might be using RADIUS for network authentication.  If you are the admin, then you can choose where things go.  If you follow the general ideas, system into /etc and individual in ~/, then almost always you will be fine.  There can be exceptions, but those generally come with instructions for where and why.

But the Admin can override pretty much anything, in commercial-quality software.

---

