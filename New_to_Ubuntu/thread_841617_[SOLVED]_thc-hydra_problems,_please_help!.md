---
title: "[SOLVED] thc-hydra problems, please help!"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Sc4Rzz on 2008-06-26
Hello ubuntu and other linux users,

trying to install thc-hydra from source today, I encountered a big problem.
so this is what happened in the terminal:
note I renamed the hydra folder.

```


sc4rzz@desktopsc4rzz:~/Desktop/hydra$ ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from http://www.openssl.org
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
sc4rzz@desktopsc4rzz:~/Desktop/hydra$ make
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
sc4rzz@desktopsc4rzz:~/Desktop/hydra$ make install
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
sc4rzz@desktopsc4rzz:~/Desktop/hydra$ 



```


Hope you can help me...

---

### Post by cariboo on 2008-06-26
It looks like you are missing a lot of dependencies. You should install the missing packages and try again. All the programs that it can't find are available in the repositories, you can use synaptic to install them.

```
openssl
SVN
SAP
ssh2

```

Search for the above and install.

Jim

---

### Post by Sc4Rzz on 2008-06-26
> **cariboo907 said:**
> It looks like you are missing a lot of dependencies. You should install the missing packages and try again. All the programs that it can't find are available in the repositories, you can use synaptic to install them.

```
openssl
SVN
SAP
ssh2

```

Search for the above and install.

Jim

Thank you Jim :)

I now have ubuntu for over a month, and I tought I got it 100% ...
you proved me wrong, thanks.

---

### Post by herot on 2008-08-14
Could you paste the code you used to install these dependencies? The search returned too many choices... I'm not sure which ones to install.

---

### Post by Sc4Rzz on 2008-08-14
> **herot said:**
> Could you paste the code you used to install these dependencies? The search returned too many choices... I'm not sure which ones to install.

I just used synaptic?
and if you're not sure wich one to choose, install them all :lolflag:

---

