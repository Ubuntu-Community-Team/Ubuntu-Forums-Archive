---
title: "compile squid3.1.19 from source, error: Neither SASL nor SASL2 found"
date: 2013-05-07
forum: Packaging and Compiling Programs
---

### Post by jimmah6786 on 2013-05-07
Hey all, 

I am trying to comiple squid3 from source to get SSL enabled. 

```
sudo apt-get build-essentials fakeroot devscripts openssl
sudo apt-get build-dep squid3
sudo apt-get source squid3
```

When I do a 
```
debuild -us -uc -b 
```
I get
```
error: Neither SASL nor SASL2 found
```

I verified I have SASL2 installed, I even did a 
```
sudo apt-get install libsasl2-2
```

Heres the last lines of the buiid error
```
configure: Linux (Netfilter) Transparent Proxy enabled
configure: Using POSIX_V6_LP64_OFF64 build environment
configure: Auth scheme modules built: basic digest ntlm negotiate
configure: Basic auth helpers built: LDAP MSNT NCSA PAM SASL SMB YP DB POP3 getpwnam squid_radius_auth multi-domain-NTLM
configure: NTLM auth helpers built: smb_lm 
configure: Negotiate auth helpers built: squid_kerb_auth
configure: Digest auth helpers built: ldap password
configure: External acl helpers built: ip_user ldap_group session unix_group wbinfo_group
checking sasl/sasl.h usability... no
checking sasl/sasl.h presence... no
checking for sasl/sasl.h... no
checking sasl.h usability... no
checking sasl.h presence... no
checking for sasl.h... no
checking for sasl_errstring in -lsasl2... no
checking for sasl_errstring in -lsasl... no
configure: error: Neither SASL nor SASL2 found
make: *** [debian/stamp-autotools] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

---

### Post by mc4man on 2013-05-07
You shouldn't get that error if libsasl2-dev (2.1.25.dfsg1-6) is installed which build-dep should of pulled in.
(your first posted command has 2 mistakes & wouldn't install anything, likely you mistyped in your post?

More of an issue would be a cppunit error (fails to find at /usr), though that could be fixed
I know nothing of this source ect. but would suspect that simply rebuilding using same rules wouldn't add the SSL support if not already enabled.
(openssl seems to be a configure option

---

### Post by Bucky Ball on 2013-05-07
*Thread moved to **General Help**.*

Unsure why you posted in Ubuntu +1. That is now for Saucy (13.10) and your question doesn't relate to Ubuntu +1. Good luck. ;)

---

### Post by jimmah6786 on 2013-05-07
> **mc4man said:**
> You shouldn't get that error if libsasl2-dev (2.1.25.dfsg1-6) is installed which build-dep should of pulled in.
(your first posted command has 2 mistakes & wouldn't install anything, likely you mistyped in your post?

More of an issue would be a cppunit error (fails to find at /usr), though that could be fixed
I know nothing of this source ect. but would suspect that simply rebuilding using same rules wouldn't add the SSL support if not already enabled.
(openssl seems to be a configure option

Sorry that's a typo it should be the sudo apt-get install.

Yes the configure option is:
```
./configure --enable-ssl --enable-ssl-crtd
```

---

### Post by jimmah6786 on 2013-05-07
I moved it to the correct section, please delete this quesiton.

---

### Post by Bucky Ball on 2013-05-07
> **jimmah6786 said:**
> I moved it to the correct section, please delete this quesiton.

? It is in the correct section. What is the link to the duplicate post? Not quite understanding ...

---

### Post by cariboo on 2013-05-07
It looks like the op created a new thread in Installation & Upgrades. I've closed that one, and any replies should continue in this thread.

---

### Post by Bucky Ball on 2013-05-07
> **cariboo907 said:**
> It looks like the op created a new thread in Installation & Upgrades. I've closed that one, and any replies should continue in this thread.

Ta.

---

### Post by Cheesemill on 2013-05-08
I think you need the sasl development files as well, not just the library...
```
sudo apt-get install libsasl2-dev
```

---

### Post by SeijiSensei on 2013-05-08
If you want to push SSL through the proxy, I assume you are aware of [SSLBump]("http://wiki.squid-cache.org/Features/SslBump").  I've tested it with 3.2.0.19, but it will not support transparent proxying until 3.3.  You must tell the client to use the proxy for SSL and, of course, install the required server certificate so the proxy doesn't generate "man-in-the-middle" errors in the browser.

If you want to use "[dynamic SSL certificate generation]("http://wiki.squid-cache.org/Features/DynamicSslCert")" you should be compiling [3.2]("http://www.squid-cache.org/Versions/v3/3.2/").

---

### Post by oldos2er on 2013-05-08
Moved to Packaging & Compiling Programs.

---

