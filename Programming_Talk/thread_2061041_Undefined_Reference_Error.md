---
title: "Undefined Reference Error"
date: 2012-09-21
forum: Programming Talk
---

### Post by funkfresh01 on 2012-09-21
I am trying the install hydra-7.3 for the first time.  I used the make and checkinstall command and both of them gave me the following output.

```

gcc -I. -O3 -lm    -o hydra  hydra.c hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o
hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o
hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-
mysql.ohydra-mssql.o hydra-xmpp.o hydra-http-proxy-urlenum.o hydra-snmp.o
hydra-cvs.o hydra-smtp.o hydra-smtp-enum.o hydra-sapr3.o hydra-ssh.o hydra-
teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o
hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-oracle-sid.o hydra-oracle.o hydra-
vmauthd.o hydra-firebird.o hydra-afp.o hydra-ncp.o hydra-http-proxy.o hydra-
http-form.o hydra-irc.o hydra-rdp.o crc32.o d3des.o bfg.o ntlm.o sasl.o hmacmd5.o
hydra-mod.o -lm -lssl -lncp -lfbclient -lidn -lpcre -lmysqlclient -lafpclient -lpq 
-lsvn_client-1 -lapr-1 -laprutil-1 -lsvn_subr-1 -lssh -lcrypto -L/usr/lib -L/usr/local/lib
-L/lib -L/lib/i386-linux-gnu -L/usr/lib/i386-linux-gnu -L/usr/lib -L/usr/lib/i386-linux-gnu
-L/usr/lib -L/usr/lib/i386-linux-gnu -I/usr/include/subversion-1 -I/usr/include/apr-1.0
 -I/usr/include/subversion-1 -I/usr/include/mysql -I/usr/include/afpfs-ng -DLIBOPENSSL 
-DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE 
-DLIBMYSQLCLIENT -DLIBAFP -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH 
-DHAVE_MATH_H
/tmp/cctN1ihm.o: In function `hydra_spawn_head':
hydra.c: (.text+0x34db): undefined reference to `service_svn'
hydra.c: (.text+0x3568 ): undefined reference to `service_smb'
hydra.c: (.text+0x3b6c): undefined reference to `service_firebird'
hydra.c: (.text+0x3bbf): undefined reference to `service_postgres'
collect2: ld returned 1 exit status
make: *** [hydra] Error 1
```Can anyone explain this? What is the remedy to this problem?  Thank you

---

### Post by cariboo on 2012-09-22
A bump for the move to Programming Talk.

---

### Post by funkfresh01 on 2012-09-23
> **cariboo907 said:**
> A bump for the move to Programming Talk.

I guess I need to know how to program then. Have you got any suggestions? I am instructed in learning C++ and Perl. Do you know any forums I can goto?:p

---

### Post by steeldriver on 2012-09-23
Usually that means you haven't linked all the correct libraries, or have attempted to link them in the wrong order (the subsidiary library must normally go after the module that calls it - unless you use library start / end groups)

```
$ gcc -O3 -o test test.c
/tmp/ccIbHuUz.o: In function `main':
test.c:(.text.startup+0x11e): undefined reference to **`sqrt'**
collect2: ld returned 1 exit status
$ 
$ gcc -O3 **-lm** -o test test.c
/tmp/ccHSA9ys.o: In function `main':
test.c:(.text.startup+0x11e): undefined reference to `sqrt'
collect2: ld returned 1 exit status
$ 
$ gcc -O3 -o test test.c** -lm**
$ 
```

---

