---
title: "URGENT: missing dependencies to install thc-hydra"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Sc4Rzz on 2008-06-26
Hello Ubuntu users,

I need some pro help..
I tried to install thc-hydra recently, and without succes.

I was missing 4 dependencies, and already installed 2 of them.
I still need ssh2 en SAP (sapr3) but they aren't in synaptic! (or not under the names ssh2 and sapr3...)

It's really urgent,, hope you can help.

the error I got:

```

sc4rzz@desktopsc4rzz:~/Desktop/hydra$ ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
sc4rzz@desktopsc4rzz:~/Desktop/hydra$ 


```

---

