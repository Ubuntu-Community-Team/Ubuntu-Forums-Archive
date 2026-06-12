---
title: "Hydra make problem"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by maruf7 on 2012-12-25
Hello,
I'm trying to install Hydra-7.3 in Ubuntu 12.04, but the make command gives the following error:

```
gcc -I. -O3 -o pw-inspector pw-inspector.c
gcc -I. -O3 -c hydra-vnc.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-pcnfs.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-rexec.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-nntp.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-socks5.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-telnet.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-cisco.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-http.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-ftp.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-imap.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-pop3.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-smb.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-icq.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-cisco-enable.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-ldap.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-mysql.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-mssql.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-xmpp.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-http-proxy-urlenum.c -DHAVE_MATH_H
gcc -I. -O3 -c hydra-snmp.c -DHAVE_MATH_H
hydra-snmp.c: In function ‘start_snmp’:
hydra-snmp.c:333:20: error: ‘C_Block’ undeclared (first use in this function)
hydra-snmp.c:333:20: note: each undeclared identifier is reported only once for each function it appears
in
hydra-snmp.c:333:28: error: expected expression before ‘)’ token
hydra-snmp.c:334:69: error: ‘symcbc’ undeclared (first use in this function)
hydra-snmp.c:334:86: error: expected expression before ‘)’ token
hydra-snmp.c:334:99: error: ‘DES_ENCRYPT’ undeclared (first use in this function)
make: *** [hydra-snmp.o] Error 1
```

Can anybody help with this issue? Thanks.

---

### Post by andrew.46 on 2012-12-25
Compiled well enough on my non-Ubuntu partition. Have you added the extras suggested in the README:

```

If you use Ubuntu, this will install supplementary libraries needed for a
few optional modules:
 apt-get install libssl-dev libssh-dev libidn11-dev libpcre3-dev \
                 libgtk2.0-dev libmysqlclient-dev libpq-dev libsvn-dev \
                 firebird2.1-dev libncp-dev
This enables all optional modules and features with the exception of Oracle,
SAP R/3 and the apple filing protocol - which you will need to download and
install from the vendor's web sites.

```

I am not familiar with this software but you may find it may not fit with the Ubuntu Forums rules? Might not hurt to get some clarification from the moderators before we get any deeper...

---

