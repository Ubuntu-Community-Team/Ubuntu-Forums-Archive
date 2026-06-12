---
title: "Problems rebuilding squid3 with ssl"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by jesse6 on 2013-08-29
I just installed squid3 and configured it to work but now I want to enable ssl and add ssl-bump to squid
This is what I've done so far
> [I]apt-get update
apt-get install openssl
apt-get install devscripts build-essential
apt-get source squid3
apt-get build-dep squid3
cd squid3-3.1.14
vi debian/rules
#added in  --enable-ssl
#added in --with-open-ssl="/etc/ssl/openssl.cnf"
debuild -us -uc[/I]

But when I run the debuild command i get an error and I'm unable to continue
Thanks


last 25 lines of executed command "[I]debuild -us -uc"
[/I]```
../../src/ssl_support.h:123:98: error: 'ASN1_STRING' was not declared in this scope../../src/ssl_support.h:123:111: error: 'cn_data' was not declared in this scope
../../src/ssl_support.h:123:119: error: expression list treated as compound expression in initializer [-fpermissive]
../../src/ssl_support.h:133:22: error: 'ASN1_TIME' was not declared in this scope
../../src/ssl_support.h:133:35: error: expected primary-expression before ',' token
../../src/ssl_support.h:133:37: error: expected primary-expression before 'char'
../../src/ssl_support.h:133:48: error: expected primary-expression before 'int'
../../src/ssl_support.h:133:55: error: expression list treated as compound expression in initializer [-fpermissive]
In file included from ../../src/squid.h:318:0,
                 from AsyncCall.cc:5:
../../src/structs.h:618:9: error: 'SSL_CTX' does not name a type
../../src/structs.h:965:5: error: 'SSL_CTX' does not name a type
../../src/structs.h:966:5: error: 'SSL_SESSION' does not name a type
make[4]: *** [AsyncCall.lo] Error 1
make[4]: Leaving directory `/etc/squid3/squid3-3.1.14/src/base'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/etc/squid3/squid3-3.1.14/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/etc/squid3/squid3-3.1.14/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/etc/squid3/squid3-3.1.14'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1348:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

---

### Post by jesse6 on 2013-08-29
I found the problem :D

Turns out installing openssl is not enough, I needed to install openssl-devel libraries

After running these commands squid is now running with ssl enabled
```
apt-get install libssl-dev
cd /etc/squid/squid3-3.1.1
debuild -us -uc
cd ..
dpkg -i squid3_3.1.14-1ubuntu0.3_amd64.deb
```

Output of squid -v
```
Squid Cache: Version 3.1.14
configure options:  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/squid3' '--srcdir=.' '--disable-maintainer-mode' '--disable-dependency-tracking' '--disable-silent-rules' '--datadir=/usr/share/squid3' '--sysconfdir=/etc/squid3' '--mandir=/usr/share/man' '--with-cppunit-basedir=/usr' '--enable-ssl' '--with-open-ssl=/etc/ssl/openssl.cnf' '--enable-inline' '--enable-async-io=8' '--enable-storeio=ufs,aufs,diskd' '--enable-removal-policies=lru,heap' '--enable-delay-pools' '--enable-cache-digests' '--enable-underscores' '--enable-icap-client' '--enable-follow-x-forwarded-for' '--enable-auth=basic,digest,ntlm,negotiate' '--enable-basic-auth-helpers=LDAP,MSNT,NCSA,PAM,SASL,SMB,YP,DB,POP3,getpwnam,squid_radius_auth,multi-domain-NTLM' '--enable-ntlm-auth-helpers=smb_lm,' '--enable-digest-auth-helpers=ldap,password' '--enable-negotiate-auth-helpers=squid_kerb_auth' '--enable-external-acl-helpers=ip_user,ldap_group,session,unix_group,wbinfo_group' '--enable-arp-acl' '--enable-esi' '--enable-zph-qos' '--disable-translation' '--with-logdir=/var/log/squid3' '--with-pidfile=/var/run/squid3.pid' '--with-filedescriptors=65536' '--with-large-files' '--with-default-user=proxy' '--enable-linux-netfilter' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2 -g -O2 -Wall' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2 -g -O2 -Wall' --with-squid=/etc/squid3/squid3-3.1.14
```

---

