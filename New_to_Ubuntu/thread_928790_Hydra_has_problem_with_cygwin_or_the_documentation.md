---
title: "Hydra has problem with cygwin or the documentation is not complete"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by boyboy400 on 2008-09-24
Hi all,
Before posting, I searched previous posts but I didn't found my answer.
I use cygwin to compile hydra (since I want to patch it I have to do so otherwise a windows version is available)
after ./configure  it says:

////////////////////////////////////////////////////////

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
... NOT found, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq) ...
... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

cygwin detected, enabling compatibility options ...
Hydra will be installed into .../bin of: /usr/local
(change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
================================================== =====================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make" 

////////////////////////////////////////////////
When I type make it gives me:
bach: make: command not found

I used sudo command but apparently it's not for cygwin.
I used also make install but it was the same.

Please help me.

---

