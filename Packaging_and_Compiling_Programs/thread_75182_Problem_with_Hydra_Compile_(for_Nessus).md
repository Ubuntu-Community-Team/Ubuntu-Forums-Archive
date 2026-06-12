---
title: "Problem with Hydra Compile (for Nessus)"
date: 2005-10-13
forum: Packaging and Compiling Programs
---

### Post by Marge on 2005-10-13
"Could not find -lssl" 

When I researched this problem I found out it could be that it couldn't find an SSL llibrary in Open SSL [I have openssl version 0.9.8.].  I'm new to Linux.  Can anyone help?  Thanks.



[email]root@ubuntu:~/Desktop/HYDRA/hydra-4.7-src.tar.gz[/email]_FILES/hydra-4.7-src # ./configu re

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please ru

n ./configure-arm or ./configure-palm respectivly

now type "make"
[email]root@ubuntu:~/Desktop/HYDRA/hydra-4.7-src.tar.gz[/email]_FILES/hydra-4.7-src # make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/ include
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/ include
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-http.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/loca l/ssl/include
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ ssl/include
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ss l/include
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/i nclude
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/in clude
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/s sl/include
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ss l/include
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/ include
gcc -I. -Wall -O2 -c crc32.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/include
gcc -I. -Wall -O2 -c d3des.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/include
gcc -I. -Wall -O2 -c md4.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/include
gcc -I. -Wall -O2 -c hydra-mod.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/inc lude
gcc -I. -Wall -O2 -c hydra.c -DLIBOPENSSL -DLIBPOSTGRES -I/usr/local/ssl/include
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nnt p.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-i map.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hyd ra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs .o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres. o hydra-rsh.o hydra-rlogin.o crc32.o d3des.o md4.o hydra-mod.o hydra.o -lm -lssl  -lpq -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib -L/usr/lib -L/usr/l ib
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status
make: *** [hydra] Error 1

---

### Post by outlook on 2005-11-04
You might go looking for [outlook express repair ](http://www.oemailrecovery.com/outlook-express-repair.html) and [recovery outlook express email](http://www.mail-repair.com/mail-recovery-service.html). I have been using it without problem since it came out.

---

### Post by spare on 2005-11-20
when i make,
.......
/usr/bin/ld: cannot find -lpq
collect2: ld returned 1 exit status
make: *** [hydra] Error 1
that's why,thank you !

---

### Post by Gouki on 2007-01-26
I know this is really old, but I'm going to post either way.

You can get the .DEB packages [here]("http://files.goukihq.org/Packages/"), including the libssh which is a requirement for Hydra.

I'm also working on a Ubuntu package, so soon a simple apt-get install thc-hydra will do the trick.

---

