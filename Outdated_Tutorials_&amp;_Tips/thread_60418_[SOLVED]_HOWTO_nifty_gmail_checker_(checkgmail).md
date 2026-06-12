---
title: "[SOLVED] HOWTO: nifty gmail checker (checkgmail)"
date: 2005-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-08-27
This howto is way outdated. Please move to jail.
Thanks.
-Arnie

---

### Post by manicka on 2005-08-27
Installation went well, but I get this error message

```
Warning: XML::Simple not found ...
Warning: Crypt::SSLeay not found ...

CheckGmail requires the above packages to run
Please download and install from CPAN (http://search.cpan.org) and try again ...
```

---

### Post by arnieboy on 2005-08-27
[QUOTE=manicka]Installation went well, but I get this error message

```
Warning: XML::Simple not found ...
Warning: Crypt::SSLeay not found ...

CheckGmail requires the above packages to run
Please download and install from CPAN (http://search.cpan.org) and try again ...
```[/QUOTE]
try the following:
```
sudo perl -MCPAN -e 'install XML::Simple'
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```
Now run gmailchecker.
These 2 modules were already installed in my system and so I didnt get the error. Thanks for pointing out the possibility of their not being installed by default though. I have suitably edited the HowTo.

---

### Post by manicka on 2005-08-27
Ok, installed Crypt::SSLeay, but when try 

```
sudo perl -MCPAN -e 'install LWP::Simple'
```

I get 

```
CPAN: Storable loaded ok
Going to read /home/manicka/.cpan/Metadata
  Database was generated on Thu, 25 Aug 2005 04:59:01 GMT
LWP::Simple is up to date.
```

and still get this error when running checkgmail

```
Warning: XML::Simple not found ...
```

---

### Post by manicka on 2005-08-27
Forget it... wrong package!

It's the simple mistakes that make us humble :D

---

### Post by arnieboy on 2005-08-27
[QUOTE=manicka]Ok, installed Crypt::SSLeay, but when try 

```
sudo perl -MCPAN -e 'install LWP::Simple'
```

I get 

```
CPAN: Storable loaded ok
Going to read /home/manicka/.cpan/Metadata
  Database was generated on Thu, 25 Aug 2005 04:59:01 GMT
LWP::Simple is up to date.
```

and still get this error when running checkgmail

```
Warning: XML::Simple not found ...
```[/QUOTE]
U typed the wrong command manicka.
the correct command is:
```
sudo perl -MCPAN -e 'install XML::Simple'
```

---

### Post by arnieboy on 2005-08-27
[QUOTE=manicka]Forget it... wrong package!

It's the simple mistakes that make us humble :D[/QUOTE]
NO problem. Hope you got it working now. Dont u find it real nifty?

---

### Post by manicka on 2005-08-27
[QUOTE=arnieboy]NO problem. Hope you got it working now. Dont u find it real nifty?[/QUOTE]
Real nifty indeed :D

[[IMG]http://img281.imageshack.us/img281/2015/checkmail2lm.jpg[/IMG]](http://imageshack.us)

---

### Post by arnieboy on 2005-08-27
[QUOTE=manicka]Real nifty indeed :D[/QUOTE]
hey what app is that tintin head in your system tray? just curious :D

---

### Post by manicka on 2005-08-27
[QUOTE=arnieboy]hey what app is that tintin head in your system tray? just curious :D[/QUOTE]
 tomboy 0.3.1-0Ubuntu6

---

### Post by arnieboy on 2005-08-27
[QUOTE=manicka]tomboy 0.3.1-0Ubuntu6[/QUOTE]
aah.. the note taking app..

---

### Post by LaSSarD on 2005-08-27
Hi, thanks for your how-to :)
When executing the 4th command (sudo perl -MCPAN -e 'install Crypt::SSLeay'), it stopped:

```
No OpenSSL installation found, usually in /usr/local/openssl
Which OpenSSL build path do you want to link against?
```

I don't know what to type here :P
Can you help me with this? :)

---

### Post by arnieboy on 2005-08-27
[QUOTE=LaSSarD]Hi, thanks for your how-to :)
When executing the 4th command (sudo perl -MCPAN -e 'install Crypt::SSLeay'), it stopped:

```
No OpenSSL installation found, usually in /usr/local/openssl
Which OpenSSL build path do you want to link against?
```

I don't know what to type here :P
Can you help me with this? :)[/QUOTE]
do the following in a new terminal window:
```
sudo apt-get install openssl
```
and then hit enter on the perl module installation step . it will automatically detect that openssl is installed.
or u can restart the installation of the perl modules again.

---

### Post by PMO6022 on 2005-08-27
[QUOTE=LaSSarD]Hi, thanks for your how-to :)
When executing the 4th command (sudo perl -MCPAN -e 'install Crypt::SSLeay'), it stopped:

```
No OpenSSL installation found, usually in /usr/local/openssl
Which OpenSSL build path do you want to link against?
```

I don't know what to type here :P
Can you help me with this? :)[/QUOTE]

I'm pretty sure you need to install libssl-dev, so open up a terminal and type
```
sudo apt-get install libssl-dev
```
Then try sudo perl -MCPAN -e 'install Crypt::SSLeay again.

---

### Post by cannibalbob on 2005-08-27
> SSLeay.c:844: error: syntax error before ')' token
SSLeay.xs:434: error: invalid type argument of `->'
SSLeay.c: In function `XS_Crypt__SSLeay__X509_get_notAfterString':
SSLeay.c:863: error: `X509' undeclared (first use in this function)
SSLeay.c:863: error: `cert' undeclared (first use in this function)
SSLeay.c:869: error: syntax error before ')' token
SSLeay.xs:442: error: invalid type argument of `->'
make: *** [SSLeay.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

any idea what this is about?

---

### Post by arnieboy on 2005-08-27
[QUOTE=cannibalbob]any idea what this is about?[/QUOTE]
did u get this error when u tried to do:
```
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```?

---

### Post by cannibalbob on 2005-08-27
[QUOTE=arnieboy]did u get this error when u tried to do:
```
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```?[/QUOTE]

yes

---

### Post by arnieboy on 2005-08-27
[QUOTE=cannibalbob]yes[/QUOTE]
though it looks like a bug in the code, it should not be a bug because its worked for quite a few of us. Please post the whole debugging info on the terminal after u press enter after typing *sudo perl -MCPAN -e 'install Crypt::SSLeay'* (the whole of it including the errors).

---

### Post by cannibalbob on 2005-08-27
CPAN: Storable loaded ok
Going to read /home/andrew/.cpan/Metadata
  Database was generated on Sat, 27 Aug 2005 21:59:32 GMT
Running install for module Crypt::SSLeay
Running make for C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gzLWP](ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gzLWP) failed with code[404] message[File 'Crypt-SSLeay-0.51.tar.gz' not found]
Fetching with Net::FTP:
  ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gzCouldn't fetch Crypt-SSLeay-0.51.tar.gz from archive.progeny.com
Fetching with LWP:
  [ftp://cpan-sj.viaverio.com/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz](ftp://cpan-sj.viaverio.com/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz)
LWP failed with code[404] message[File 'Crypt-SSLeay-0.51.tar.gz' not found]
Fetching with Net::FTP:
  [ftp://cpan-sj.viaverio.com/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz](ftp://cpan-sj.viaverio.com/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz)
Couldn't fetch Crypt-SSLeay-0.51.tar.gz from cpan-sj.viaverio.com
Fetching with LWP:
  [ftp://cpan.calvin.edu/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz](ftp://cpan.calvin.edu/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz)
LWP failed with code[400] message[FTP return code 000]
Fetching with Net::FTP:
  ftp://cpan.calvin.edu/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gzCouldn't fetch Crypt-SSLeay-0.51.tar.gz from cpan.calvin.edu

Trying with "/usr/bin/lynx -source" to get
    [ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz](ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz)
CPAN: Compress::Zlib loaded ok
CPAN: Digest::MD5 loaded ok

Trying with "/usr/bin/lynx -source" to get
    [ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/CHECKSUMS](ftp://archive.progeny.com/CPAN/authors/id/C/CH/CHAMAS/CHECKSUMS)
Checksum for /home/andrew/.cpan/sources/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz ok
Scanning cache /home/andrew/.cpan/build for sizes
Crypt-SSLeay-0.51/
Crypt-SSLeay-0.51/t/
Crypt-SSLeay-0.51/t/net_ssl.t
Crypt-SSLeay-0.51/t/ssl_context.t
Crypt-SSLeay-0.51/lib/
Crypt-SSLeay-0.51/lib/Crypt/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/MainContext.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Conn.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/X509.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Err.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/CTX.pm
Crypt-SSLeay-0.51/lib/Net/
Crypt-SSLeay-0.51/lib/Net/SSL.pm
Crypt-SSLeay-0.51/certs/
Crypt-SSLeay-0.51/certs/ca-bundle.crt
Crypt-SSLeay-0.51/certs/notacakeynopass.pem
Crypt-SSLeay-0.51/certs/notacacert.pem
Crypt-SSLeay-0.51/MANIFEST
Crypt-SSLeay-0.51/typemap
Crypt-SSLeay-0.51/MANIFEST.SKIP
Crypt-SSLeay-0.51/SSLeay.pm
Crypt-SSLeay-0.51/CHANGES
Crypt-SSLeay-0.51/lwp-ssl-test
Crypt-SSLeay-0.51/net_ssl_test
Crypt-SSLeay-0.51/SSLeay.xs
Crypt-SSLeay-0.51/README
Crypt-SSLeay-0.51/Makefile.PL

  CPAN.pm: Going to build C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz

No OpenSSL installation found, usually in /usr/local/openssl
Which OpenSSL build path do you want to link against?  Apparently no SSLeay installation at ''
Are you sure you got it correct????

================================================
BUILD INFORMATION
================================================

ssl dir:
libraries:      -lssl -lcrypto -lgcc -lRSAglue -lrsaref
include dir:    /include
ssl header:     ssl.h
ssl candidate:  ; /include

================================================

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgcc
Note (probably harmless): No library found for -lRSAglue
Note (probably harmless): No library found for -lrsaref
Writing Makefile for Crypt::SSLeay
cp lib/Crypt/SSLeay/X509.pm blib/lib/Crypt/SSLeay/X509.pm
cp lib/Net/SSL.pm blib/lib/Net/SSL.pm
cp SSLeay.pm blib/lib/Crypt/SSLeay.pm
cp lib/Crypt/SSLeay/MainContext.pm blib/lib/Crypt/SSLeay/MainContext.pm
cp lib/Crypt/SSLeay/Conn.pm blib/lib/Crypt/SSLeay/Conn.pm
cp lib/Crypt/SSLeay/CTX.pm blib/lib/Crypt/SSLeay/CTX.pm
cp lib/Crypt/SSLeay/Err.pm blib/lib/Crypt/SSLeay/Err.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  SSLeay.xs > SSLeay.xsc && mv SSLeay.xsc SSLeay.c
cc -c  -I/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"  SSLeay.c
In file included from SSLeay.xs:25:
crypt_ssleay_version.h:1:17: ssl.h: No such file or directory
crypt_ssleay_version.h:2:20: crypto.h: No such file or directory
In file included from crypt_ssleay_version.h:3,
                 from SSLeay.xs:25:
/usr/include/err.h:37: error: syntax error before '(' token
crypt_ssleay_version.h:4:18: rand.h: No such file or directory
crypt_ssleay_version.h:5:20: pkcs12.h: No such file or directory
SSLeay.xs:43: error: syntax error before '*' token
SSLeay.xs: In function `InfoCallback':
SSLeay.xs:48: error: `where' undeclared (first use in this function)
SSLeay.xs:48: error: (Each undeclared identifier is reported only once
SSLeay.xs:48: error: for each function it appears in.)
SSLeay.xs:48: error: `SSL_ST_MASK' undeclared (first use in this function)
SSLeay.xs:50: error: `SSL_ST_CONNECT' undeclared (first use in this function)
SSLeay.xs:52: error: `SSL_ST_ACCEPT' undeclared (first use in this function)
SSLeay.xs:57: error: `SSL_CB_LOOP' undeclared (first use in this function)
SSLeay.xs:58: error: `s' undeclared (first use in this function)
SSLeay.xs:59: error: `SSL_CB_ALERT' undeclared (first use in this function)
SSLeay.xs:61: error: `SSL_CB_READ' undeclared (first use in this function)
SSLeay.xs:63: error: `ret' undeclared (first use in this function)
SSLeay.xs:66: error: `SSL_CB_EXIT' undeclared (first use in this function)
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_new':
SSLeay.c:120: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:120: error: `RETVAL' undeclared (first use in this function)
SSLeay.xs:104: error: `ctx' undeclared (first use in this function)
SSLeay.xs:133: error: `SSL_OP_ALL' undeclared (first use in this function)
SSLeay.xs:136: error: `SSL_VERIFY_NONE' undeclared (first use in this function)
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_free':
SSLeay.c:173: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:173: error: `ctx' undeclared (first use in this function)
SSLeay.c:177: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_set_cipher_list':
SSLeay.c:194: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:194: error: `ctx' undeclared (first use in this function)
SSLeay.c:201: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_use_certificate_file':
SSLeay.c:219: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:219: error: `ctx' undeclared (first use in this function)
SSLeay.c:227: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_use_PrivateKey_file':
SSLeay.c:245: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:245: error: `ctx' undeclared (first use in this function)
SSLeay.c:253: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_use_pkcs12_file':
SSLeay.c:271: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:271: error: `ctx' undeclared (first use in this function)
SSLeay.xs:172: error: `EVP_PKEY' undeclared (first use in this function)
SSLeay.xs:172: error: `pkey' undeclared (first use in this function)
SSLeay.xs:173: error: `X509' undeclared (first use in this function)
SSLeay.xs:173: error: `cert' undeclared (first use in this function)
SSLeay.xs:174: error: `ca' undeclared (first use in this function)
SSLeay.xs:175: error: `PKCS12' undeclared (first use in this function)
SSLeay.xs:175: error: `p12' undeclared (first use in this function)
SSLeay.c:286: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_check_private_key':
SSLeay.c:325: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:325: error: `ctx' undeclared (first use in this function)
SSLeay.c:331: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__CTX_set_verify':
SSLeay.c:349: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:349: error: `ctx' undeclared (first use in this function)
SSLeay.c:358: error: syntax error before ')' token
SSLeay.xs:217: error: `SSL_VERIFY_NONE' undeclared (first use in this function)
SSLeay.xs:221: error: `SSL_VERIFY_PEER' undeclared (first use in this function)
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_new':
SSLeay.c:389: error: `SSL_CTX' undeclared (first use in this function)
SSLeay.c:389: error: `ctx' undeclared (first use in this function)
SSLeay.xs:235: error: `SSL' undeclared (first use in this function)
SSLeay.xs:235: error: `ssl' undeclared (first use in this function)
SSLeay.c:394: error: `RETVAL' undeclared (first use in this function)
SSLeay.c:398: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_free':
SSLeay.c:443: error: `SSL' undeclared (first use in this function)
SSLeay.c:443: error: `ssl' undeclared (first use in this function)
SSLeay.c:447: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_set_fd':
SSLeay.c:464: error: `SSL' undeclared (first use in this function)
SSLeay.c:464: error: `ssl' undeclared (first use in this function)
SSLeay.c:471: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_connect':
SSLeay.c:489: error: `SSL' undeclared (first use in this function)
SSLeay.c:489: error: `ssl' undeclared (first use in this function)
SSLeay.c:495: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_accept':
SSLeay.c:513: error: `SSL' undeclared (first use in this function)
SSLeay.c:513: error: `ssl' undeclared (first use in this function)
SSLeay.c:519: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_write':
SSLeay.c:537: error: `SSL' undeclared (first use in this function)
SSLeay.c:537: error: `ssl' undeclared (first use in this function)
SSLeay.c:549: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_read':
SSLeay.c:590: error: `SSL' undeclared (first use in this function)
SSLeay.c:590: error: `ssl' undeclared (first use in this function)
SSLeay.c:603: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_get_peer_certificate':
SSLeay.c:655: error: `SSL' undeclared (first use in this function)
SSLeay.c:655: error: `ssl' undeclared (first use in this function)
SSLeay.c:656: error: `X509' undeclared (first use in this function)
SSLeay.c:656: error: `RETVAL' undeclared (first use in this function)
SSLeay.c:660: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_get_verify_result':
SSLeay.c:679: error: `SSL' undeclared (first use in this function)
SSLeay.c:679: error: `ssl' undeclared (first use in this function)
SSLeay.c:684: error: syntax error before ')' token
SSLeay.xs:377: error: `X509_V_OK' undeclared (first use in this function)
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_get_shared_ciphers':
SSLeay.c:704: error: `SSL' undeclared (first use in this function)
SSLeay.c:704: error: `ssl' undeclared (first use in this function)
SSLeay.c:713: error: syntax error before ')' token
SSLeay.xs:388: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function `XS_Crypt__SSLeay__Conn_get_cipher':
SSLeay.c:732: error: `SSL' undeclared (first use in this function)
SSLeay.c:732: error: `ssl' undeclared (first use in this function)
SSLeay.c:738: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__X509_free':
SSLeay.c:757: error: `X509' undeclared (first use in this function)
SSLeay.c:757: error: `cert' undeclared (first use in this function)
SSLeay.c:761: error: syntax error before ')' token
SSLeay.c: In function `XS_Crypt__SSLeay__X509_subject_name':
SSLeay.c:778: error: `X509' undeclared (first use in this function)
SSLeay.c:778: error: `cert' undeclared (first use in this function)
SSLeay.c:786: error: syntax error before ')' token
SSLeay.xs:412: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function `XS_Crypt__SSLeay__X509_issuer_name':
SSLeay.c:808: error: `X509' undeclared (first use in this function)
SSLeay.c:808: error: `cert' undeclared (first use in this function)
SSLeay.c:816: error: syntax error before ')' token
SSLeay.xs:424: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function `XS_Crypt__SSLeay__X509_get_notBeforeString':
SSLeay.c:838: error: `X509' undeclared (first use in this function)
SSLeay.c:838: error: `cert' undeclared (first use in this function)
SSLeay.c:844: error: syntax error before ')' token
SSLeay.xs:434: error: invalid type argument of `->'
SSLeay.c: In function `XS_Crypt__SSLeay__X509_get_notAfterString':
SSLeay.c:863: error: `X509' undeclared (first use in this function)
SSLeay.c:863: error: `cert' undeclared (first use in this function)
SSLeay.c:869: error: syntax error before ')' token
SSLeay.xs:442: error: invalid type argument of `->'
make: *** [SSLeay.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

---

### Post by arnieboy on 2005-08-27
looks like a dependency problem to me. are u sure u have openssl installed? to double check do a:
```
sudo apt-get install openssl libssl-dev
```
and try to compile the SSLeay module again. when it asks for the OpenSSL path type:
/usr/include/openssl
Hope this helps.

---

### Post by cannibalbob on 2005-08-27
awesome. works now, thx.  :)

---

### Post by arnieboy on 2005-08-27
[QUOTE=cannibalbob]awesome. works now, thx.  :)[/QUOTE]
glad i could help :)

---

### Post by Paulus on 2005-08-28
a quick perhaps silly question;  I recently took out my Cd-Rom drive for cosmetic reasons- lol.  so when attempting to install 
openssl and ncftp the installer requires the ubuntu cd... Is there around using the cd?

---

### Post by manicka on 2005-08-28
[QUOTE=Paulus]a quick perhaps silly question;  I recently took out my Cd-Rom drive for cosmetic reasons- lol.  so when attempting to install 
openssl and ncftp the installer requires the ubuntu cd... Is there around using the cd?[/QUOTE]
 Remove the cd as one of your sources.

sudo gedit /etc/apt/sources.list

Place a hash in front of the cdrom entry 

# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

save

refresh apt

sudo apt-get update

all should be well

---

### Post by christooss on 2005-08-28
Thanks man for this howto. This was the only thing missing in Ubuntu. Thanks

---

### Post by Paulus on 2005-08-28
your the man!   thanks for that, this program really is excellent thanks to [arnieboy]("http://member.php?u=12261") :)


[url="http://imageshack.us"]
[/url]

---

### Post by manicka on 2005-08-28
Paulus, you've posted a screenshot showing your kde-look password

---

### Post by christooss on 2005-08-28
```
Button image functions are disabled

Please upgrade to Gtk v2.6 or later
and/or update Gtk-pearl bindings

```

How can I get rid of this massage in preferences window?

---

### Post by lothar_m on 2005-08-28
[QUOTE=christooss]```
Button image functions are disabled

Please upgrade to Gtk v2.6 or later
and/or update Gtk-pearl bindings

```

How can I get rid of this massage in preferences window?[/QUOTE]


same question here.

By the away.... great job on this tutorial!

---

### Post by ilmw on 2005-08-28
thanks! excellent!

just curious: gmail has pop function. why don't we just use evolution to retrieve messages?

---

### Post by manicka on 2005-08-28
[QUOTE=ilmw]thanks! excellent!

just curious: gmail has pop function. why don't we just use evolution to retrieve messages?[/QUOTE]
 I believe that gmail works best as it's designed to be used - a web based app. 
Using Evolution with gmail makes it clunky, IMO.

---

### Post by Heliode on 2005-08-28
Worked great for me, thanks! I like the way it shows the contents of new messages when you hold the mouse over the tray icon.

---

### Post by traherom on 2005-08-28
Works for me too! Thanks for the howto...

---

### Post by majikstreet on 2005-08-28
Hi, 
When I run checkgmail, I get this error:
```

majikstreet@oreo:~/checkgmail-1.3$ ./checkgmail
CheckGmail v1.3
Copyright \uffff 2005 Owen Marshall

Warning: LWP::UserAgent not found ...
Warning: Crypt::SSLeay not found ...

CheckGmail requires the above packages to run
Please download and install from CPAN (http://search.cpan.org) and try again ...


```

I installed like you said, but at the end of most of the installs it said that the make test failed and won't install without force.

majikstreet

---

### Post by arnieboy on 2005-08-28
[QUOTE=christooss]```
Button image functions are disabled

Please upgrade to Gtk v2.6 or later
and/or update Gtk-pearl bindings

```

How can I get rid of this massage in preferences window?[/QUOTE]
in order to get rid of that message we need to upgrade to GTK-2.6 which is yet unavailable on hoary. I dont think that message gets too much in the way though. when it gets enabled some day, u will be able to choose custom icons for "connected", "disconnected" and "new mail"

---

### Post by christooss on 2005-08-28
I have breezy :P

---

### Post by arnieboy on 2005-08-28
[QUOTE=christooss]I have breezy :P[/QUOTE]
in a day or two, I will install breezy on another partition and look into this issue if nobody finds any solution to it by then.

---

### Post by arnieboy on 2005-08-28
[QUOTE=majikstreet]Hi, 
When I run checkgmail, I get this error:
```

majikstreet@oreo:~/checkgmail-1.3$ ./checkgmail
CheckGmail v1.3
Copyright \uffff 2005 Owen Marshall

Warning: LWP::UserAgent not found ...
Warning: Crypt::SSLeay not found ...

CheckGmail requires the above packages to run
Please download and install from CPAN (http://search.cpan.org) and try again ...


```

I installed like you said, but at the end of most of the installs it said that the make test failed and won't install without force.

majikstreet[/QUOTE]

did u install the dependencies (openssl and libssl-dev) before installing the perl modules? Please follow my HowTo step by step. The modules do not have any bugs which would preveent them from being installed.  My first guess would be that u dont have the dependencies installed. when u try and install Crypt::SSLeay, does it say OpenSSL build path not found or something similar? if u already have openssl and libssl-dev installed, please put in "/usr/include/openssl" as the path when it asks for the build path of openssl.

---

### Post by arnieboy on 2005-08-28
[QUOTE=Paulus]your the man!   thanks for that, this program really is excellent thanks to arnieboy :)[/QUOTE]
Hey glad I cud be of some help Paul but I do hope you have changed your kde-look password by now. lol :)

---

### Post by Weav on 2005-08-28
Wow sweet up and running thanks for the very clear guide!!

On a side note on page 3 Paulus posted his desktop and i have to say its bea-utiful.
I was wondering how to get that bottom icon MAC-OSX like bar, and then his theme looked different in a different font. Also he made his desktop just overall smaller. ANyone have any info on how to do these things?

Thanks again  :smile:

---

### Post by manicka on 2005-08-28
[QUOTE=Weav]
I was wondering how to get that bottom icon MAC-OSX like bar, and then his theme looked different in a different font. Also he made his desktop just overall smaller. ANyone have any info on how to do these things?
[/QUOTE]
On your top panel just right click on the panel and choose properties.

Orientation: Bottom (change the bottom bar to Top if needed)

Uncheck expand

Change the size to whatever you like.

-------------------------------------------------

I'd say his desktop is smaller because the screenshot was resized with gimp before posting

-------------------------------------------------

Fonts: Sytem-->Preferences --> Font

---

### Post by byen on 2005-08-28
thanks arnie... works like a charm.
got to tell you..when i saw the other thread where you stated
[QUOTE=arnieboy]well so much said, I must say I love ubuntuforums for the things that I have been able to get from it and more because of what I have been able to give it back. so I will continue to offer techical and troubleshooting support on these forums. thats something I promise.[/QUOTE]
I wasnt sure you meant it...but whoa...im impressed. Thanks!

---

### Post by majikstreet on 2005-08-28
[QUOTE=arnieboy]did u install the dependencies (openssl and libssl-dev) before installing the perl modules? Please follow my HowTo step by step. The modules do not have any bugs which would preveent them from being installed.  My first guess would be that u dont have the dependencies installed. when u try and install Crypt::SSLeay, does it say OpenSSL build path not found or something similar? if u already have openssl and libssl-dev installed, please put in "/usr/include/openssl" as the path when it asks for the build path of openssl.[/QUOTE]
 root@oreo:/home/majikstreet # apt-get install libssl-dev
Reading package lists... Done
Building dependency tree... Done
libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@oreo:/home/majikstreet #
 and
root@oreo:/home/majikstreet # apt-get install libssl-dev
Reading package lists... Done
Building dependency tree... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@oreo:/home/majikstreet #

Hmmmm--- I did follow the howto step by step.....

Oh well.... Guess I can't install it then lol.

---

### Post by Weav on 2005-08-28
[QUOTE=manicka]On your top panel just right click on the panel and choose properties.

Orientation: Bottom (change the bottom bar to Top if needed)

Uncheck expand

Change the size to whatever you like.

-------------------------------------------------

I'd say his desktop is smaller because the screenshot was resized with gimp before posting

-------------------------------------------------

Fonts: Sytem-->Preferences --> Font[/QUOTE]

sweet thanks a lot any info on the Mac-OSX bar?

---

### Post by manicka on 2005-08-28
[QUOTE=Weav]sweet thanks a lot any info on the Mac-OSX bar?[/QUOTE]
 The Mac-OSX bar effect is achieved by fiddling with the gnome-panel settings as suggested. Play with the background settings to make it transparent.
The icons in Paulus' theme are [NuoveXT](http://nuovext.pwsp.net/). I also use these as my default... very nice :)

---

### Post by arnieboy on 2005-08-28
[QUOTE=majikstreet]Oh well.... Guess I can't install it then lol.[/QUOTE]
your guess is wrong. U should be able to install it. here u just gave me the debugging info for the installation of the dependencies. Please send me the whole debugging info for ```
sudo perl -MCPAN -e 'install Crypt::SSLeay'
``` (after u type this command and press enter). one question here. why are u working as root and installing it as root? any specific reason?

---

### Post by arnieboy on 2005-08-28
[QUOTE=byen]thanks arnie... works like a charm.
got to tell you..when i saw the other thread where you stated

I wasnt sure you meant it...but whoa...im impressed. Thanks![/QUOTE]
My intention is not to impress anyone here though I must thank u for saying that. I just want to keep doing my bit to help more and more people realize why linux is the best thing thats ever happened to computers and Ubuntu is the best distro around. the more u help people understand and troubleshoot problems, the more they learn. the more they learn, the more they tell their friends and ubuntu marches steadily towards world domination.

---

### Post by LaSSarD on 2005-08-28
Thanks arnieboy and PMO6022. I did sudo apt-get install openssl libssl-dev and it worked perfectly. :)

Thanks for the how-to again :D

btw, can I change the icons that checkgmail uses?

---

### Post by Weav on 2005-08-28
[QUOTE=manicka]The Mac-OSX bar effect is achieved by fiddling with the gnome-panel settings as suggested. Play with the background settings to make it transparent.
The icons in Paulus' theme are [NuoveXT](http://nuovext.pwsp.net/). I also use these as my default... very nice :)[/QUOTE]
Cool manicka thanks for all your help! My desktop is looking a lot better including the gmail notifier in the top corner!  :grin: 

[[IMG]http://img356.imageshack.us/img356/8206/screenshot5fr.th.jpg[/IMG]](http://img356.imageshack.us/my.php?image=screenshot5fr.jpg)

---

### Post by cutOff on 2005-08-29
Worked like a charm. Thanks a lot!

---

### Post by manicka on 2005-08-29
[QUOTE=Weav]Cool manicka thanks for all your help! My desktop is looking a lot better including the gmail notifier in the top corner!  :grin: 

[[IMG]http://img356.imageshack.us/img356/8206/screenshot5fr.th.jpg[/IMG]](http://img356.imageshack.us/my.php?image=screenshot5fr.jpg)[/QUOTE]
 very nice :D

---

### Post by cutOff on 2005-08-29
[QUOTE=Heliode]Worked great for me, thanks! I like the way it shows the contents of new messages when you hold the mouse over the tray icon.[/QUOTE]
hmm.. I don't seem to get that feature. It shows an empty little box though.

---

### Post by graabein on 2005-08-29
Hi, I really want this but I got some errors. Maybe someone can help out?

```
$ sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ca-certificates
The following NEW packages will be installed:
  libgtk2-trayicon-perl libssl-dev lynx ncftp openssl
0 upgraded, 5 newly installed, 0 to remove and 6 not upgraded.
Need to get 5735kB of archives.
After unpacking 15.2MB of additional disk space will be used.
Get:1 ftp://ftp.uninett.no hoary/universe libgtk2-trayicon-perl 0.04-1 [17.6kB]
Get:2 ftp://ftp.uninett.no hoary/main libssl-dev 0.9.7e-3 [2491kB]
Get:3 ftp://ftp.uninett.no hoary/main lynx 2.8.5-2 [1855kB]
Get:4 ftp://ftp.uninett.no hoary/universe ncftp 2:3.1.8-1 [471kB]
Get:5 ftp://ftp.uninett.no hoary/main openssl 0.9.7e-3 [901kB]
Fetched 5735kB in 2m36s (36.6kB/s)
E: Could not open file /var/cache/apt/archives/libgtk2-trayicon-perl_0.04-1_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libgtk2-trayicon-perl_0.04-1_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptorE: Could not open file /var/cache/apt/archives/libssl-dev_0.9.7e-3_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libssl-dev_0.9.7e-3_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
Preconfiguring packages ...
dpkg: error processing /var/cache/apt/archives/libgtk2-trayicon-perl_0.04-1_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libssl-dev_0.9.7e-3_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package lynx.
(Reading database ... 115282 files and directories currently installed.)
Unpacking lynx (from .../archives/lynx_2.8.5-2_i386.deb) ...
Selecting previously deselected package ncftp.
Unpacking ncftp (from .../ncftp_2%3a3.1.8-1_i386.deb) ...
Selecting previously deselected package openssl.
Unpacking openssl (from .../openssl_0.9.7e-3_i386.deb) ...
Creating directory /etc/ssl
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2-trayicon-perl_0.04-1_i386.deb
 /var/cache/apt/archives/libssl-dev_0.9.7e-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
$ sudo perl -MCPAN -e 'install Bundle::LWP'
<snip>
Warning: lynx not found in PATH
Where is your lynx program? []
```

---

### Post by arnieboy on 2005-08-29
do the following:
```
sudo apt-get clean
```
followed by the installation of the debs :
```
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev
```
this should install the debs w/o problems and then the perl modules will install flawlessly as well.

---

### Post by byen on 2005-08-29
> the more they learn, the more they tell their friends and ubuntu marches steadily towards world domination I have to agree..the only reason I have managed to switched from a 100% MS user to a 100% linux user, is people like you in these forums. though i still post questions...i do help others out too...so this cycle seems to be working perfectly! but world domination...LOL...we dont wanna end up like MS do we...
..........................come to think of it...what the hell...why not! GO Ubuntu!

---

### Post by graabein on 2005-08-29
Thanks arnieboy! I got it to work now.

---

### Post by majikstreet on 2005-08-29
I was working as root then because instead of sudo, I like to do sudo su instead-- just less typing for me.....

The output is:
majikstreet@oreo:~$ sudo perl -MCPAN -e 'install Crypt::SSLeay'
Password:
CPAN: Storable loaded ok
Going to read /home/majikstreet/.cpan/Metadata
  Database was generated on Sun, 28 Aug 2005 03:07:58 GMT
LWP not available
CPAN: Net::FTP loaded ok
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
Going to read /home/majikstreet/.cpan/sources/authors/01mailrc.txt.gz
LWP not available
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
Going to read /home/majikstreet/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Mon, 29 Aug 2005 12:01:00 GMT
  HTTP::Date not available
LWP not available
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
Going to read /home/majikstreet/.cpan/sources/modules/03modlist.data.gz
Going to write /home/majikstreet/.cpan/Metadata
Running install for module Crypt::SSLeay
Running make for C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/majikstreet/.cpan/sources/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz ok
Scanning cache /home/majikstreet/.cpan/build for sizes
Crypt-SSLeay-0.51/
Crypt-SSLeay-0.51/t/
Crypt-SSLeay-0.51/t/net_ssl.t
Crypt-SSLeay-0.51/t/ssl_context.t
Crypt-SSLeay-0.51/lib/
Crypt-SSLeay-0.51/lib/Crypt/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/MainContext.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Conn.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/X509.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Err.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/CTX.pm
Crypt-SSLeay-0.51/lib/Net/
Crypt-SSLeay-0.51/lib/Net/SSL.pm
Crypt-SSLeay-0.51/certs/
Crypt-SSLeay-0.51/certs/ca-bundle.crt
Crypt-SSLeay-0.51/certs/notacakeynopass.pem
Crypt-SSLeay-0.51/certs/notacacert.pem
Crypt-SSLeay-0.51/MANIFEST
Crypt-SSLeay-0.51/typemap
Crypt-SSLeay-0.51/MANIFEST.SKIP
Crypt-SSLeay-0.51/SSLeay.pm
Crypt-SSLeay-0.51/CHANGES
Crypt-SSLeay-0.51/lwp-ssl-test
Crypt-SSLeay-0.51/net_ssl_test
Crypt-SSLeay-0.51/SSLeay.xs
Crypt-SSLeay-0.51/README
Crypt-SSLeay-0.51/Makefile.PL
Removing previously used /home/majikstreet/.cpan/build/Crypt-SSLeay-0.51

  CPAN.pm: Going to build C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz

Found OpenSSL (version OpenSSL 0.9.7) installed at /usr
Which OpenSSL build path do you want to link against? [/usr]

================================================
BUILD INFORMATION
================================================

ssl dir:        /usr
libraries:      -lssl -lcrypto -lgcc -lRSAglue -lrsaref
include dir:    /usr/include
ssl header:     openssl/ssl.h
ssl candidate:  /usr; /usr/include/openssl; OpenSSL 0.9.7

================================================

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgcc
Note (probably harmless): No library found for -lRSAglue
Note (probably harmless): No library found for -lrsaref
Writing Makefile for Crypt::SSLeay
cp lib/Crypt/SSLeay/X509.pm blib/lib/Crypt/SSLeay/X509.pm
cp lib/Net/SSL.pm blib/lib/Net/SSL.pm
cp SSLeay.pm blib/lib/Crypt/SSLeay.pm
cp lib/Crypt/SSLeay/MainContext.pm blib/lib/Crypt/SSLeay/MainContext.pm
cp lib/Crypt/SSLeay/Conn.pm blib/lib/Crypt/SSLeay/Conn.pm
cp lib/Crypt/SSLeay/CTX.pm blib/lib/Crypt/SSLeay/CTX.pm
cp lib/Crypt/SSLeay/Err.pm blib/lib/Crypt/SSLeay/Err.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  SSLeay.xs > SSLeay.xsc && mv SSLeay.xsc SSLeay.c
cc -c  -I/usr/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"   SSLeay.c
/bin/sh: cc: command not found
make: *** [SSLeay.o] Error 127
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
majikstreet@oreo:~$




(sorry for not getting back earlier!)

majikstreet

---

### Post by arnieboy on 2005-08-29
[QUOTE=majikstreet]cc -c  -I/usr/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"   SSLeay.c
/bin/sh: cc: command not found
make: *** [SSLeay.o] Error 127
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible[/QUOTE]
I think a 
```
sudo apt-get install gcc
```
will solve the problem for u. install gcc and compile the perl module again.

---

### Post by Paulus on 2005-08-29
lol, loving this.  I removed the image for obvious reasons, damm i'm dumb.
Btw for anyone interested the bar i used is the engage bar from e17- which is getting better and better!
Here's another screenie with my font settings which makes it all smaller and more winblowz like :/

btw i did gimp the previous shot!

p.s I don't mean to hiijack the thread

[[IMG]http://img110.imageshack.us/img110/4889/screenshot3vt.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=screenshot3vt.jpg)

---

### Post by Weav on 2005-08-30
[QUOTE=Paulus]lol, loving this.  I removed the image for obvious reasons, damm i'm dumb.
Btw for anyone interested the bar i used is the engage bar from e17- which is getting better and better!
Here's another screenie with my font settings which makes it all smaller and more winblowz like :/

btw i did gimp the previous shot!

p.s I don't mean to hiijack the thread

[[IMG]http://img110.imageshack.us/img110/4889/screenshot3vt.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=screenshot3vt.jpg)[/QUOTE]
wow thats one sweet looking desktop did you just follow the e17 how to and then downloaded the engage bar?

---

### Post by Paulus on 2005-08-30
yeah i used smoons repro, downloaded the whole of e17 (make sure u get engage too) and simply ran engage in gnome!

 ```
engage -W 900 -T 0 -I 1 -i 1 -e software -H 115 -s 37 -Z 2.0 -S 5 -R 55 
``` 

:o

---

### Post by hippyjim on 2005-09-01
Sorry - ignore this post - i read the thread through (missing all the bits about pointless desktop candy - c'mon guys this stuff is hard enough to follow!) and i needed gcc.


Ok, I'm a bit stuck.

I've tried this through, and it genersates loads of errors. At the first "perl" step, I get:

"Bundle summary: The following items in bundle Bundle::LWP had installation
problems:
  MIME::Base64 HTML::Parser"

I get similar errors with al lthe other steps, and of course the notifier script itsekf tells me I haven't got all sorts of things installed.

I suspect I answered one of the questions wrong (I didn't understand any of them - I don't write perl) although I went with the defaults for them all.

Anyone got any ideas?

---

### Post by arnieboy on 2005-09-01
[QUOTE=hippyjim]Sorry - ignore this post - i read the thread through (missing all the bits about pointless desktop candy - c'mon guys this stuff is hard enough to follow!) and i needed gcc.[/QUOTE]

good to know that u got it. u shd have deleted the rest of your post or put it in italics or sumthin. I thot you were still getting errors.

---

### Post by majikstreet on 2005-09-03
/me will try that then re-run your instructions again......

/me has been on irc too much.

---

### Post by majikstreet on 2005-09-03
[QUOTE=majikstreet]/me will try that then re-run your instructions again......

/me has been on irc too much.[/QUOTE]
 it works great!

---

### Post by GameManK on 2005-09-03
works great in KDE!

however, before i install all this stuff on my main computer, i'd like to know what i'm doing answering all those questions for PERL. It asks stuff like when to check the cache (on startup or never) and to pick URLs to fetch from, etc. and i'd like to know what all of this does.
thanks

---

### Post by arnieboy on 2005-09-03
[QUOTE=GameManK]works great in KDE!

however, before i install all this stuff on my main computer, i'd like to know what i'm doing answering all those questions for PERL. It asks stuff like when to check the cache (on startup or never) and to pick URLs to fetch from, etc. and i'd like to know what all of this does.
thanks[/QUOTE]
which of the questions did u not understand? most of them were about the paths of dependencies. once u get all of them right , the plugins install flawlessly.

---

### Post by GameManK on 2005-09-04
after the questions about dependencies, it asks something about checking the cache and fetching something from URL's

---

### Post by arnieboy on 2005-09-04
[QUOTE=GameManK]after the questions about dependencies, it asks something about checking the cache and fetching something from URL's[/QUOTE]
it downloads the perl modules before it installs them, u do realize that I hope? The urls are to that effect.

---

### Post by GameManK on 2005-09-04
[QUOTE=arnieboy]it downloads the perl modules before it installs them, u do realize that I hope? The urls are to that effect.[/QUOTE]

for some reason i was thinking it downloads before the config thing and the cache thing confused me

thanks for the great how-to

---

### Post by cutOff on 2005-09-12
I've just upgrade to Breezy and noticed that checkgmail doesn't work anymore. In order to solve this issue, should I repeat all the steps??

Thanks

---

### Post by manicka on 2005-09-12
[QUOTE=cutOff]I've just upgrade to Breezy and noticed that checkgmail doesn't work anymore. In order to solve this issue, should I repeat all the steps??

Thanks[/QUOTE]
 breezy has it's own little app called gmail-notify that does a similar job. However it does have a bug in it at this stage and isn't logging in properly. Hopefully it will be fixed in the next couple of days.

---

### Post by krusbjorn on 2005-09-12
Got this to work in breezy without a hitch. Thanks arnav for the how to!

---

### Post by cutOff on 2005-09-12
[QUOTE=manicka]breezy has it's won little app called gmail-notify that does a similar job. However it does have a bug in it at this stage and isn't logging in properly. Hopefully it will be fixed in the next couple of days.[/QUOTE]
Cool. Nice to know it. Thanks for the info. I'll give it a try.

---

### Post by mwdowns on 2005-09-12
I've followed the tutorial, but I've gotten stuck with an error after the first "perl -MCPAN" command.  I get the following error:> 
--20:12:09--  [ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY.gz](ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY.gz)
  (try:20) => `-'
Connecting to ftp.perl.org[163.143.1.21]:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Giving up.

Issuing "/usr/bin/ftp -n"
Not connected.
Local directory now /root/.cpan/sources
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY](ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch MIRRORED.BY
CPAN.pm needs at least one URL where it can fetch CPAN files from.

Please enter your CPAN site: []


Any ideas what I should be doing?

---

### Post by doc_holiday on 2005-09-12
Great!!

My desklet an kcheckgmail where giving my wrong username and password since yesterday. This works!!

---

### Post by arnieboy on 2005-09-13
[QUOTE=krusbjorn]Got this to work in breezy without a hitch. Thanks arnav for the how to![/QUOTE]
hey Johannes U are welcome  :)

---

### Post by arnieboy on 2005-09-13
[QUOTE=mwdowns]I've followed the tutorial, but I've gotten stuck with an error after the first "perl -MCPAN" command.  I get the following error:

Any ideas what I should be doing?[/QUOTE]
there was an error in connecting to the download mirror. did u try again later?

---

### Post by arnieboy on 2005-09-13
[QUOTE=cutOff]I've just upgrade to Breezy and noticed that checkgmail doesn't work anymore. In order to solve this issue, should I repeat all the steps??

Thanks[/QUOTE]
the perl modules probably got overwritten when u upgraded to breezy. u shd try installing them once again from start.

---

### Post by cutOff on 2005-09-13
[QUOTE=arnieboy]the perl modules probably got overwritten when u upgraded to breezy. u shd try installing them once again from start.[/QUOTE]
I don't know how but working again  :grin:

---

### Post by perlmonger on 2005-09-13
[QUOTE=arnieboy]
Now do the following:
```
tar -xjf checkgmail-1.3.tar.bz2
```
now a folder called checkgmail-1.3 will be created in your home folder and inside it will be the checkgmail perl binary which u need to add to system-->preferences-->sessions-->startup programs 
The path of the executable would be */home/user_name/checkgmail-1.3/checkgmail*
U can also open a nautilus window and double click on /home/user_name/checkgmail-1.3/checkgmail to make it run (or run it from terminal). next time u boot in to GNOME it will start automatically and u will see how nifty and unobtrusive it is. 
**please note:** "user_name" is the name of your user account.
[/QUOTE]

This is a great how-to. Could you maybe update it to work with KDE as well? The system-->preferences-->sessions-->startup programs piece is different for KDE and I don't know how to add startup programs to KDE.

Thanks

---

### Post by manicka on 2005-09-13
To make an autostart in KDE

go to the directory /home/user./kde/Autostart
Right clicke inside the directory and choose  'Link to Application' from the menu
In the general tab you can call it what you like e.g. checkgmail
In the Application tab enter the path to the executable (e.g /home/user_name/checkgmail-1.3/checkgmail) in the command field and whatever you like in name and description fields. Click Ok when your done.

---

### Post by GameManK on 2005-09-15
[QUOTE=arnieboy]> 
Code:

Button image functions are disabled

Please upgrade to Gtk v2.6 or later
and/or update Gtk-pearl bindings


How can I get rid of this massage in preferences window?


in order to get rid of that message we need to upgrade to GTK-2.6 which is yet unavailable on hoary. I dont think that message gets too much in the way though. when it gets enabled some day, u will be able to choose custom icons for "connected", "disconnected" and "new mail"[/QUOTE]

looking at the version column in kynaptic for libgtk2 i think i have 2.6.4, but that message is there anyways

i want to make the background of the icon transparent. would i be able to do it if that custom icon feature worked correctly, or am i missing something with the "set tray background" button? it's annoying changing that background whenever i change my wallpaper

---

### Post by bored2k on 2005-09-15
> Your ftp_proxy?
Your http_proxy?
Your no_proxy?
You have no /home/reb/.cpan/sources/MIRRORED.BY
  I'm trying to fetch one
LWP not available
CPAN: Net::FTP loaded ok
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY](ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY)
Couldn't cwd pub/CPAN at /usr/share/perl/5.8/CPAN.pm line 2260, <STDIN> line 27.Fetching with Net::FTP
  [ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY.gz](ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY.gz)

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY](ftp://ftp.perl.org/pub/CPAN/MIRRORED.BY)

It just stalls :(

---

### Post by bored2k on 2005-09-15
```
sudo perl -MCPAN -e 'install Bundle::LWP'
CPAN: Storable loaded ok
LWP not available

Trying with "/usr/bin/lynx -source" to get
    [http://www.cpan.org/MIRRORED.BY/authors/01mailrc.txt.gz](http://www.cpan.org/MIRRORED.BY/authors/01mailrc.txt.gz)

gzip: /home/reb/.cpan/sources/authors/01mailrc.txt: not in gzip format
Going to read /home/reb/.cpan/sources/authors/01mailrc.txt.gz

Trying with "/usr/bin/lynx -source" to get
    [http://www.cpan.org/MIRRORED.BY/modules/02packages.details.txt.gz](http://www.cpan.org/MIRRORED.BY/modules/02packages.details.txt.gz)

gzip: /home/reb/.cpan/sources/modules/02packages.details.txt: not in gzip format
Going to read /home/reb/.cpan/sources/modules/02packages.details.txt.gz
Warning: Your /home/reb/.cpan/sources/modules/02packages.details.txt.gz does not contain a Line-Count header.
Please check the validity of the index file by comparing it to more
than one CPAN mirror. I'll continue but problems seem likely to
happen.
Warning: Your /home/reb/.cpan/sources/modules/02packages.details.txt.gz does not contain a Last-Updated header.
Please check the validity of the index file by comparing it to more
than one CPAN mirror. I'll continue but problems seem likely to
happen.

Trying with "/usr/bin/lynx -source" to get
    [http://www.cpan.org/MIRRORED.BY/modules/03modlist.data.gz](http://www.cpan.org/MIRRORED.BY/modules/03modlist.data.gz)

gzip: /home/reb/.cpan/sources/modules/03modlist.data: not in gzip format
Going to read /home/reb/.cpan/sources/modules/03modlist.data.gz
Can't locate object method "data" via package "CPAN::Modulelist" (perhaps you forgot to load "CPAN::Modulelist"?) at (eval 11) line 1.
 at /usr/share/perl/5.8/CPAN.pm line 3407
        CPAN::Index::rd_modlist('CPAN::Index', '/home/reb/.cpan/sources/modules/03modlist.data.gz') called at /usr/share/perl/5.8/CPAN.pm line 3129
        CPAN::Index::reload('CPAN::Index') called at /usr/share/perl/5.8/CPAN.pm line 675
        CPAN::exists('CPAN=HASH(0x86d03b0)', 'CPAN::Bundle', 'Bundle::LWP') called at /usr/share/perl/5.8/CPAN.pm line 1926
        CPAN::Shell::expand('CPAN::Shell', 'Bundle', 'Bundle::LWP') called at /usr/share/perl/5.8/CPAN.pm line 1840
        CPAN::Shell::expandany('CPAN::Shell', 'Bundle::LWP') called at /usr/share/perl/5.8/CPAN.pm line 2078
        CPAN::Shell::rematein('CPAN::Shell', 'install', 'Bundle::LWP') called at /usr/share/perl/5.8/CPAN.pm line 2165
        CPAN::Shell::install('CPAN::Shell', 'Bundle::LWP') called at /usr/share/perl/5.8/CPAN.pm line 79
        CPAN::AUTOLOAD('Bundle::LWP') called at -e line 1

```

---

### Post by mwdowns on 2005-09-16
Hello again.  I tried installing this again (this time after a fresh install of breezy).  But, I couldn't get past the first MCPAN command.  I got the following error:> libwww-perl-5.803/t/net/cgi-bin/test
libwww-perl-5.803/t/net/cgi-bin/slowread
libwww-perl-5.803/t/net/cgi-bin/timeout
libwww-perl-5.803/t/net/proxy.t
libwww-perl-5.803/t/net/http-post.t
libwww-perl-5.803/t/net/moved.t
libwww-perl-5.803/t/net/http-timeout.t
libwww-perl-5.803/t/net/config.pl.dist
libwww-perl-5.803/t/net/mirror.t
libwww-perl-5.803/t/robot/
libwww-perl-5.803/t/robot/rules.t
libwww-perl-5.803/t/robot/ua.t
libwww-perl-5.803/t/robot/ua-get.t
libwww-perl-5.803/t/robot/rules-dbm.t
libwww-perl-5.803/t/README
libwww-perl-5.803/t/html/
libwww-perl-5.803/t/html/form-param.t
libwww-perl-5.803/t/html/form.t
libwww-perl-5.803/t/TEST
libwww-perl-5.803/bin/
libwww-perl-5.803/bin/lwp-rget
libwww-perl-5.803/bin/lwp-mirror
libwww-perl-5.803/bin/lwp-download
libwww-perl-5.803/bin/lwp-request
libwww-perl-5.803/Makefile.PL
libwww-perl-5.803/talk-to-ourself
libwww-perl-5.803/lwptut.pod
libwww-perl-5.803/MANIFEST
libwww-perl-5.803/README.SSL
libwww-perl-5.803/Changes
libwww-perl-5.803/AUTHORS
libwww-perl-5.803/README
libwww-perl-5.803/lwpcook.pod
MIME::Base64 is up to date.
Digest::MD5 is up to date.
Running install for module URI
Running make for G/GA/GAAS/URI-1.35.tar.gz

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/G/GA/GAAS/URI-1.35.tar.gz](ftp://ftp.kddilabs.jp/CPAN/authors/id/G/GA/GAAS/URI-1.35.tar.gz)

gzip: /home/matt/.cpan/sources/authors/id/G/GA/GAAS/URI-1.35.tar: not in gzip format
Checksum for /home/matt/.cpan/sources/authors/id/G/GA/GAAS/URI-1.35.tar.gz ok
URI-1.35/
URI-1.35/t/
URI-1.35/t/ldap.t
URI-1.35/t/rsync.t
URI-1.35/t/clone.t
URI-1.35/t/pop.t
URI-1.35/t/heuristic.t
URI-1.35/t/roytest2.html
URI-1.35/t/old-base.t
URI-1.35/t/generic.t
URI-1.35/t/news.t
URI-1.35/t/file.t
URI-1.35/t/roytest1.html
URI-1.35/t/ftp.t
URI-1.35/t/urn-isbn.t
URI-1.35/t/abs.t
URI-1.35/t/storable-test.pl
URI-1.35/t/mix.t
URI-1.35/t/split.t
URI-1.35/t/urn-oid.t
URI-1.35/t/mailto.t
URI-1.35/t/roytest5.html
URI-1.35/t/sip.t
URI-1.35/t/data.t
URI-1.35/t/rfc2732.t
URI-1.35/t/old-relbase.t
URI-1.35/t/http.t
URI-1.35/t/roytest4.html
URI-1.35/t/query.t
URI-1.35/t/mms.t
URI-1.35/t/rel.t
URI-1.35/t/roy-test.t
URI-1.35/t/old-absconf.t
URI-1.35/t/storable.t
URI-1.35/t/query-param.t
URI-1.35/t/escape.t
URI-1.35/t/roytest3.html
URI-1.35/t/old-file.t
URI-1.35/t/rtsp.t
URI-1.35/URI/
URI-1.35/URI/mailto.pm
URI-1.35/URI/_generic.pm
URI-1.35/URI/_ldap.pm
URI-1.35/URI/urn.pm
URI-1.35/URI/file.pm
URI-1.35/URI/_login.pm
URI-1.35/URI/Heuristic.pm
URI-1.35/URI/rtsp.pm
URI-1.35/URI/file/
URI-1.35/URI/file/Base.pm
URI-1.35/URI/file/OS2.pm
URI-1.35/URI/file/Mac.pm
URI-1.35/URI/file/QNX.pm
URI-1.35/URI/file/FAT.pm
URI-1.35/URI/file/Win32.pm
URI-1.35/URI/file/Unix.pm
URI-1.35/URI/snews.pm
URI-1.35/URI/rsync.pm
URI-1.35/URI/URL.pm
URI-1.35/URI/_foreign.pm
URI-1.35/URI/tn3270.pm
URI-1.35/URI/ftp.pm
URI-1.35/URI/Escape.pm
URI-1.35/URI/urn/
URI-1.35/URI/urn/oid.pm
URI-1.35/URI/urn/isbn.pm
URI-1.35/URI/data.pm
URI-1.35/URI/Split.pm
URI-1.35/URI/_segment.pm
URI-1.35/URI/_query.pm
URI-1.35/URI/rtspu.pm
URI-1.35/URI/ldapi.pm
URI-1.35/URI/QueryParam.pm
URI-1.35/URI/rlogin.pm
URI-1.35/URI/https.pm
URI-1.35/URI/pop.pm
URI-1.35/URI/http.pm
URI-1.35/URI/sips.pm
URI-1.35/URI/mms.pm
URI-1.35/URI/nntp.pm
URI-1.35/URI/sip.pm
URI-1.35/URI/ldaps.pm
URI-1.35/URI/news.pm
URI-1.35/URI/ssh.pm
URI-1.35/URI/ldap.pm
URI-1.35/URI/telnet.pm
URI-1.35/URI/_server.pm
URI-1.35/URI/WithBase.pm
URI-1.35/URI/gopher.pm
URI-1.35/URI/_userpass.pm
URI-1.35/URI.pm
URI-1.35/rfc2396.txt
URI-1.35/Makefile.PL
URI-1.35/uri-test
URI-1.35/MANIFEST
URI-1.35/Changes
URI-1.35/README

  CPAN.pm: Going to build G/GA/GAAS/URI-1.35.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for URI
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Net::FTP is up to date.
Running install for module HTML::Tagset
Running make for S/SB/SBURKE/HTML-Tagset-3.04.tar.gz

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/S/SB/SBURKE/HTML-Tagset-3.04.tar.gz](ftp://ftp.kddilabs.jp/CPAN/authors/id/S/SB/SBURKE/HTML-Tagset-3.04.tar.gz)

gzip: /home/matt/.cpan/sources/authors/id/S/SB/SBURKE/HTML-Tagset-3.04.tar: not in gzip format

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/S/SB/SBURKE/CHECKSUMS](ftp://ftp.kddilabs.jp/CPAN/authors/id/S/SB/SBURKE/CHECKSUMS)
Checksum for /home/matt/.cpan/sources/authors/id/S/SB/SBURKE/HTML-Tagset-3.04.tar.gz ok
HTML-Tagset-3.04/
HTML-Tagset-3.04/META.yml
HTML-Tagset-3.04/t/
HTML-Tagset-3.04/t/01_old_junk.t
HTML-Tagset-3.04/t/00_about_verbose.t
HTML-Tagset-3.04/MANIFEST
HTML-Tagset-3.04/ChangeLog
HTML-Tagset-3.04/lib/
HTML-Tagset-3.04/lib/HTML/
HTML-Tagset-3.04/lib/HTML/Tagset.pm
HTML-Tagset-3.04/MANIFEST.SKIP
HTML-Tagset-3.04/Makefile.PL
HTML-Tagset-3.04/README

  CPAN.pm: Going to build S/SB/SBURKE/HTML-Tagset-3.04.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for HTML::Tagset
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module HTML::Parser
Running make for G/GA/GAAS/HTML-Parser-3.45.tar.gz

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/G/GA/GAAS/HTML-Parser-3.45.tar.gz](ftp://ftp.kddilabs.jp/CPAN/authors/id/G/GA/GAAS/HTML-Parser-3.45.tar.gz)

gzip: /home/matt/.cpan/sources/authors/id/G/GA/GAAS/HTML-Parser-3.45.tar: not in gzip format
Checksum for /home/matt/.cpan/sources/authors/id/G/GA/GAAS/HTML-Parser-3.45.tar.gz ok
HTML-Parser-3.45/
HTML-Parser-3.45/t/
HTML-Parser-3.45/t/xml-mode.t
HTML-Parser-3.45/t/textarea.t
HTML-Parser-3.45/t/filter-methods.t
HTML-Parser-3.45/t/crashme.t
HTML-Parser-3.45/t/handler-eof.t
HTML-Parser-3.45/t/unicode-bom.t
HTML-Parser-3.45/t/argspec-bad.t
HTML-Parser-3.45/t/dtext.t
HTML-Parser-3.45/t/callback.t
HTML-Parser-3.45/t/entities.t
HTML-Parser-3.45/t/argspec.t
HTML-Parser-3.45/t/comment.t
HTML-Parser-3.45/t/declaration.t
HTML-Parser-3.45/t/offset.t
HTML-Parser-3.45/t/handler.t
HTML-Parser-3.45/t/plaintext.t
HTML-Parser-3.45/t/case-sensitive.t
HTML-Parser-3.45/t/cases.t
HTML-Parser-3.45/t/marked-sect.t
HTML-Parser-3.45/t/filter.t
HTML-Parser-3.45/t/tokeparser.t
HTML-Parser-3.45/t/linkextor-rel.t
HTML-Parser-3.45/t/entities2.t
HTML-Parser-3.45/t/skipped-text.t
HTML-Parser-3.45/t/linkextor-base.t
HTML-Parser-3.45/t/default.t
HTML-Parser-3.45/t/headparser.t
HTML-Parser-3.45/t/uentities.t
HTML-Parser-3.45/t/headparser-http.t
HTML-Parser-3.45/t/script.t
HTML-Parser-3.45/t/stack-realloc.t
HTML-Parser-3.45/t/magic.t
HTML-Parser-3.45/t/options.t
HTML-Parser-3.45/t/attr-encoded.t
HTML-Parser-3.45/t/unicode.t
HTML-Parser-3.45/t/argspec2.t
HTML-Parser-3.45/t/ignore.t
HTML-Parser-3.45/t/largetags.t
HTML-Parser-3.45/t/unbroken-text.t
HTML-Parser-3.45/t/msie-compat.t
HTML-Parser-3.45/t/api_version.t
HTML-Parser-3.45/t/parsefile.t
HTML-Parser-3.45/t/parser.t
HTML-Parser-3.45/t/process.t
HTML-Parser-3.45/t/pullparser.t
HTML-Parser-3.45/eg/
HTML-Parser-3.45/eg/hlc
HTML-Parser-3.45/eg/hanchors
HTML-Parser-3.45/eg/htextsub
HTML-Parser-3.45/eg/htitle
HTML-Parser-3.45/eg/hstrip
HTML-Parser-3.45/eg/hrefsub
HTML-Parser-3.45/eg/hform
HTML-Parser-3.45/eg/hdump
HTML-Parser-3.45/eg/htext
HTML-Parser-3.45/lib/
HTML-Parser-3.45/lib/HTML/
HTML-Parser-3.45/lib/HTML/Entities.pm
HTML-Parser-3.45/lib/HTML/PullParser.pm
HTML-Parser-3.45/lib/HTML/Filter.pm
HTML-Parser-3.45/lib/HTML/TokeParser.pm
HTML-Parser-3.45/lib/HTML/LinkExtor.pm
HTML-Parser-3.45/lib/HTML/HeadParser.pm
HTML-Parser-3.45/util.c
HTML-Parser-3.45/Makefile.PL
HTML-Parser-3.45/hints/
HTML-Parser-3.45/hints/solaris.pl
HTML-Parser-3.45/Parser.pm
HTML-Parser-3.45/TODO
HTML-Parser-3.45/MANIFEST
HTML-Parser-3.45/tokenpos.h
HTML-Parser-3.45/Changes
HTML-Parser-3.45/mkhctype
HTML-Parser-3.45/Parser.xs
HTML-Parser-3.45/mkpfunc
HTML-Parser-3.45/hparser.c
HTML-Parser-3.45/README
HTML-Parser-3.45/hparser.h
HTML-Parser-3.45/typemap

  CPAN.pm: Going to build G/GA/GAAS/HTML-Parser-3.45.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite HTML::Tagset 3 not found.
Writing Makefile for HTML::Parser
---- Unsatisfied dependencies detected during [G/GA/GAAS/HTML-Parser-3.45.tar.gz] -----
    HTML::Tagset
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]
Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module HTML::HeadParser
Running make for G/GA/GAAS/HTML-Parser-3.45.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/HTML-Parser-3.45
  Delayed until after prerequisites
Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module LWP
Running make for G/GA/GAAS/libwww-perl-5.803.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/libwww-perl-5.803

  CPAN.pm: Going to build G/GA/GAAS/libwww-perl-5.803.tar.gz


This package comes with some sample programs that I can try
to install in /usr/bin.

   Note that you can avoid these questions by passing
   the '-n' option to 'Makefile.PL'.

Do you want to install lwp-request? [y]
Do you want to install lwp-mirror? [y]
Do you want to install lwp-rget? [y]
Do you want to install lwp-download? [y]

The lwp-request program will use the name it is invoked with to
determine what HTTP method to use.  I can set up alias for the most
common HTTP methods.  These alias are also installed in
/usr/bin.

Do you want to install the GET alias? [n]
Do you want to install the HEAD alias? [n]
Do you want to install the POST alias? [n]

Checking for URI........... failed
Can't locate URI.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at Makefile.PL line 148, <STDIN> line 7.

The URI module must be installed.  WWW without URIs would not
be that great :-)

Checking for HTML::Parser.. failed
Can't locate HTML/HeadParser.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at Makefile.PL line 167, <STDIN> line 7.

The HTML::Parser is needed to extract correct base URI information from
HTML so that we can resolve relative links correctly.  The HTML::Form
module also need HTML::TokeParser to work.

Checking for MIME::Base64.. ok
Checking for Net::FTP...... ok
Checking for Digest::MD5 .. ok
The missing modules can be obtained from CPAN.  Visit
<URL:http://www.perl.com/CPAN/> to find a CPAN site near you.


Checking if your kit is complete...
Looks good
Warning: prerequisite Compress::Zlib 1.10 not found.
Warning: prerequisite HTML::Parser 3.33 not found.
Warning: prerequisite URI 1.10 not found.
Writing Makefile for libwww-perl
---- Unsatisfied dependencies detected during [G/GA/GAAS/libwww-perl-5.803.tar.gz] -----
    URI
    Compress::Zlib
    HTML::Parser
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]
Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Bundle summary: The following items in bundle Bundle::LWP had installation
problems:
  URI HTML::Tagset HTML::Parser HTML::HeadParser LWP
Running install for module URI
Running make for G/GA/GAAS/URI-1.35.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/URI-1.35
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Compress::Zlib
Running make for P/PM/PMQS/Compress-Zlib-1.38.tar.gz

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/P/PM/PMQS/Compress-Zlib-1.38.tar.gz](ftp://ftp.kddilabs.jp/CPAN/authors/id/P/PM/PMQS/Compress-Zlib-1.38.tar.gz)

gzip: /home/matt/.cpan/sources/authors/id/P/PM/PMQS/Compress-Zlib-1.38.tar: not in gzip format

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.kddilabs.jp/CPAN/authors/id/P/PM/PMQS/CHECKSUMS](ftp://ftp.kddilabs.jp/CPAN/authors/id/P/PM/PMQS/CHECKSUMS)
Checksum for /home/matt/.cpan/sources/authors/id/P/PM/PMQS/Compress-Zlib-1.38.tar.gz ok
Compress-Zlib-1.38/
Compress-Zlib-1.38/zlib-src/
Compress-Zlib-1.38/zlib-src/compress.c
Compress-Zlib-1.38/zlib-src/inffixed.h
Compress-Zlib-1.38/zlib-src/zlib.h
Compress-Zlib-1.38/zlib-src/zutil.h
Compress-Zlib-1.38/zlib-src/inftrees.h
Compress-Zlib-1.38/zlib-src/gzio.c
Compress-Zlib-1.38/zlib-src/zconf.h
Compress-Zlib-1.38/zlib-src/crc32.h
Compress-Zlib-1.38/zlib-src/uncompr.c
Compress-Zlib-1.38/zlib-src/zutil.c
Compress-Zlib-1.38/zlib-src/deflate.c
Compress-Zlib-1.38/zlib-src/inftrees.c
Compress-Zlib-1.38/zlib-src/crc32.c
Compress-Zlib-1.38/zlib-src/deflate.h
Compress-Zlib-1.38/zlib-src/inffast.h
Compress-Zlib-1.38/zlib-src/adler32.c
Compress-Zlib-1.38/zlib-src/trees.c
Compress-Zlib-1.38/zlib-src/infback.c
Compress-Zlib-1.38/zlib-src/trees.h
Compress-Zlib-1.38/zlib-src/inflate.h
Compress-Zlib-1.38/zlib-src/inffast.c
Compress-Zlib-1.38/zlib-src/inflate.c
Compress-Zlib-1.38/examples/
Compress-Zlib-1.38/examples/gzgrep
Compress-Zlib-1.38/examples/filtdef
Compress-Zlib-1.38/examples/filtinf
Compress-Zlib-1.38/examples/gzstream
Compress-Zlib-1.38/examples/gzcat
Compress-Zlib-1.38/Zlib.xs
Compress-Zlib-1.38/Changes
Compress-Zlib-1.38/fallback.h
Compress-Zlib-1.38/MANIFEST
Compress-Zlib-1.38/typemap
Compress-Zlib-1.38/t/
Compress-Zlib-1.38/t/05gzsetp.t
Compress-Zlib-1.38/t/03examples.t
Compress-Zlib-1.38/t/06gzdopen.t
Compress-Zlib-1.38/t/01version.t
Compress-Zlib-1.38/t/02zlib.t
Compress-Zlib-1.38/t/04encoding.t
Compress-Zlib-1.38/META.yml
Compress-Zlib-1.38/fallback.xs
Compress-Zlib-1.38/ANNOUNCE
Compress-Zlib-1.38/Zlib.pm
Compress-Zlib-1.38/config.in
Compress-Zlib-1.38/Makefile.PL
Compress-Zlib-1.38/README

  CPAN.pm: Going to build P/PM/PMQS/Compress-Zlib-1.38.tar.gz

Parsing config.in...
Building Zlib enabled
Looks Good.
Up/Downgrade complete.
Checking if your kit is complete...
Looks good
Writing Makefile for Compress::Zlib
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module HTML::Parser
Running make for G/GA/GAAS/HTML-Parser-3.45.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/HTML-Parser-3.45

  CPAN.pm: Going to build G/GA/GAAS/HTML-Parser-3.45.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for G/GA/GAAS/libwww-perl-5.803.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/libwww-perl-5.803

  CPAN.pm: Going to build G/GA/GAAS/libwww-perl-5.803.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module HTML::Tagset
Running make for S/SB/SBURKE/HTML-Tagset-3.04.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/HTML-Tagset-3.04
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for G/GA/GAAS/HTML-Parser-3.45.tar.gz
  Is already unwrapped into directory /home/matt/.cpan/build/HTML-Parser-3.45
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
matt@ubuntu:~$

Any ideas what I need to do?

Thanks.

---

### Post by arnieboy on 2005-09-16
which version of gcc do u have installed? make sure u have gcc 3.x (where x is the latest version number) installed. I dont have breezy on my system and I havent tested it yet but from I know, its completely built with gcc 4. I think this is a problem with trying to compile the modules with gcc 4.0.. I am not sure whether 3.x and 4 can coexist on the same system.. 
I know people who have upgraded to breezy running this successfully because they did not recompile the modules. However, for fresh installs of breezy I think the version of gcc(4) is creating a problem. check and let me know.

---

### Post by LaSSarD on 2005-09-16
I've recently upgraded to Breezy and checkgmail works fine :D

---

### Post by arnieboy on 2005-09-16
[QUOTE=LaSSarD]I've recently upgraded to Breezy and checkgmail works fine :D[/QUOTE]
yes but u might run into problems if u have a fresh breezy install and u try to compile the perl modules.. since I dont have breezy installed, I cant look into this problem yet. anyway, enjoy your gmail checker on breezy :)

---

### Post by rimmer on 2005-09-16
[QUOTE=arnieboy]checkgmail is a nifty perl program which sits in your system tray and checks your gmail account. looks almost like its windows counterpart.
there are other alternatives like the firefox gmail checker (got to have firefox open for that), kcheckgmail (the latest version has dependency problems with ubuntu libs) and the gdesklets sidecandy gmail checker which also is pretty good. but if u want a gmail checker which sits unobtrusively in ur system tray and works flawlessly u should check this one out. Herez how to install it:
first download the compressed file from a mirror of your choice:
```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.3.tar.bz2?download
```
Now do the following:
```
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev gcc
```
Next do the following:
```
sudo perl -MCPAN -e 'install Bundle::LWP'
sudo perl -MCPAN -e 'install Crypt::Simple'
sudo perl -MCPAN -e 'install XML::Simple'
sudo perl -MCPAN -e 'install Crypt::SSLeay'

```All the above commands will configure your system and ask a bunch of simple questions which should be easy enough to answer (in my case almost all of them were defaults). They will install the perl modules.
Now do the following:
```
tar -xjf checkgmail-1.3.tar.bz2
```
now a folder called checkgmail-1.3 will be created in your home folder and inside it will be the checkgmail perl binary which u need to add to system-->preferences-->sessions-->startup programs 
The path of the executable would be */home/user_name/checkgmail-1.3/checkgmail*
U can also open a nautilus window and double click on /home/user_name/checkgmail-1.3/checkgmail to make it run (or run it from terminal). next time u boot in to GNOME it will start automatically and u will see how nifty and unobtrusive it is. 
**please note:** "user_name" is the name of your user account.

EDIT: this is a tip for those who dont share their comps with others. dont log out of gmail in your web browser (just close the browser window) and everytime gmailchecker informs u of new mail, one single click on the app will take you to your inbox without your having to type your user name and password in the browser again.

**Please NOTE**: I have not tried this on Breezy because I have not upgraded to Breezy yet. It does work out of the box if u upgrade to Breezy and do not recompile the perl modules. However, if u make a fresh Breezy install and face problems while compiling the perl modules, I for one person will not be able to troubleshoot your problems. I am waiting for the final release of Breezy (or atleast RC1) before I upgrade to it.[/QUOTE]

Nice how to man !

To save the hassel why not use Gkrellm.

Set up your e-mail for pop3, With Gmail It's pretty easy 
Then set up Gkrellm (you can get it from apt-get) and every mail you get Gkrellm will let you know .
Then Install and configure Evolution, and away you go,

---

### Post by christooss on 2005-09-16
gkrellm is not a tray application. And tray application is what we need. rimmer why not using a gdesklet over gkrellm? You don't need any evolution configuration.

---

### Post by mwdowns on 2005-09-19
[QUOTE=arnieboy]which version of gcc do u have installed? make sure u have gcc 3.x (where x is the latest version number) installed. I dont have breezy on my system and I havent tested it yet but from I know, its completely built with gcc 4. I think this is a problem with trying to compile the modules with gcc 4.0.. I am not sure whether 3.x and 4 can coexist on the same system.. 
I know people who have upgraded to breezy running this successfully because they did not recompile the modules. However, for fresh installs of breezy I think the version of gcc(4) is creating a problem. check and let me know.[/QUOTE]

I checked (sorry for the late reply to this...been busy), and I am running gcc 4.0.  Should I install the 3.0 version?  How much will that mess with my system?

---

### Post by wawa on 2005-09-19
Works like a charm    :smile: 

Thanks

---

### Post by christooss on 2005-09-23
Hello I accidantilly selected server which is not avalibel How can I change server which I chose when I run

sudo perl -MCPAN -e 'install Bundle::LWP'

---

### Post by arnieboy on 2005-09-23
[QUOTE=christooss]Hello I accidantilly selected server which is not avalibel How can I change server which I chose when I run

sudo perl -MCPAN -e 'install Bundle::LWP'[/QUOTE]
do a:
```
sudo rm -rf $HOME/.cpan
```

and if u are installing this on breezy follow my updated howto (first post)

---

### Post by christooss on 2005-09-23
[QUOTE=arnieboy]do a:
```
sudo rm -rf $HOME/.cpan
```

and if u are installing this on breezy follow my updated howto (first post)[/QUOTE]
 No a sudo rm -rf /etc/CPAN/config.* did the thing. if you remove cpan from home you only remove downloaded files. thanks anyway

---

### Post by arnieboy on 2005-09-23
[QUOTE=christooss]No a sudo rm -rf /etc/CPAN/config.* did the thing. if you remove cpan from home you only remove downloaded files. thanks anyway[/QUOTE]
Thats correct. thanks for making the correction.

---

### Post by christooss on 2005-09-23
Thanks for the corrections. gmail checker works fine on clean installation of breezy.

Thanks

---

### Post by cwhitmore75 on 2005-09-24
```
christian@linuxmain:~$ sudo perl -MCPAN -e 'install Bundle::LWP'
CPAN: Storable loaded ok
Going to read /home/christian/.cpan/Metadata
Warning: Found only 0 objects in /home/christian/.cpan/Metadata
LWP not available
CPAN: Net::FTP loaded ok
Fetching with Net::FTP:
  [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz)

Trying with "/usr/bin/lynx -source" to get
    [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz)

Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Can't Access `ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz'
Alert!: Unable to access document.

lynx: Can't access startfile

System call "/usr/bin/lynx -source "ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz"  > /home/christian/.cpan/sources/authors/01mailrc.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/authors/01mailrc.txt.gz] doesn't exist

Trying with "/usr/bin/ncftpget" to get
    [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz)
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
ncftpget: cannot open cpan.llarian.net: remote host refused connection.

System call "cd /home/christian/.cpan/sources/authors && /usr/bin/ncftpget "ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz" "
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/authors/01mailrc.txt.gz] doesn't exist

Trying with "/usr/bin/wget -O -" to get
    [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz)
--03:34:22--  [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz)
           => `-'
Resolving cpan.llarian.net... 209.221.142.118
Connecting to cpan.llarian.net[209.221.142.118]:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz"  > /home/christian/.cpan/sources/authors/01mailrc.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/authors/01mailrc.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/christian/.cpan/sources/authors
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz](ftp://cpan.llarian.net/pub/CPAN/authors/01mailrc.txt.gz).

Please check, if the URLs I found in your configuration file
([ftp://cpan.llarian.net/pub/CPAN/](ftp://cpan.llarian.net/pub/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch authors/01mailrc.txt.gz
LWP not available
Fetching with Net::FTP:
  [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz)

Trying with "/usr/bin/lynx -source" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz)

Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Can't Access `ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz'Alert!: Unable to access document.

lynx: Can't access startfile

System call "/usr/bin/lynx -source "ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz"  > /home/christian/.cpan/sources/modules/02packages.details.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/02packages.details.txt.gz] doesn't exist

Trying with "/usr/bin/ncftpget" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz)
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
ncftpget: cannot open cpan.llarian.net: remote host refused connection.

System call "cd /home/christian/.cpan/sources/modules && /usr/bin/ncftpget "ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz" "
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/02packages.details.txt.gz] doesn't exist

Trying with "/usr/bin/wget -O -" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz)
--03:35:08--  [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz)
           => `-'
Resolving cpan.llarian.net... 209.221.142.118
Connecting to cpan.llarian.net[209.221.142.118]:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz"  > /home/christian/.cpan/sources/modules/02packages.details.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/02packages.details.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/christian/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz](ftp://cpan.llarian.net/pub/CPAN/modules/02packages.details.txt.gz).

Please check, if the URLs I found in your configuration file
([ftp://cpan.llarian.net/pub/CPAN/](ftp://cpan.llarian.net/pub/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/02packages.details.txt.gz
LWP not available
Fetching with Net::FTP:
  [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz)

Trying with "/usr/bin/lynx -source" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz)

Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Looking up cpan.llarian.net
Making FTP connection to cpan.llarian.net
Alert!: Unable to connect to FTP host.
Can't Access `ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz'
Alert!: Unable to access document.

lynx: Can't access startfile

System call "/usr/bin/lynx -source "ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz"  > /home/christian/.cpan/sources/modules/03modlist.data"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/03modlist.data.gz] doesn't exist

Trying with "/usr/bin/ncftpget" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz)
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
Could not connect to cpan.llarian.net: Connection refused.
ncftpget: cannot open cpan.llarian.net: remote host refused connection.

System call "cd /home/christian/.cpan/sources/modules && /usr/bin/ncftpget "ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz" "
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/03modlist.data.gz] doesn't exist

Trying with "/usr/bin/wget -O -" to get
    [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz)
--03:35:52--  [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz)
           => `-'
Resolving cpan.llarian.net... 209.221.142.118
Connecting to cpan.llarian.net[209.221.142.118]:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz"  > /home/christian/.cpan/sources/modules/03modlist.data"
returned status 1 (wstat 256)
Warning: expected file [/home/christian/.cpan/sources/modules/03modlist.data.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/christian/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz](ftp://cpan.llarian.net/pub/CPAN/modules/03modlist.data.gz).

Please check, if the URLs I found in your configuration file
([ftp://cpan.llarian.net/pub/CPAN/](ftp://cpan.llarian.net/pub/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/03modlist.data.gz
Going to write /home/christian/.cpan/Metadata
Warning: Cannot install Bundle::LWP, don't know what it is.
Try the command

    i /Bundle::LWP/

to find objects with matching identifiers.
``` 

Think I may have deleted .cpan by accident and the result is the above.    :???:  Is there a way I can start over?

---

### Post by christooss on 2005-09-24
Do a sudo -rf /etc/CPAN/config.*

---

### Post by christooss on 2005-09-24
[QUOTE=christooss]Do a sudo -rf /etc/CPAN/config.*[/QUOTE]
 and sudo -rf .cpan

---

### Post by cwhitmore75 on 2005-09-26
> Quote:
Originally Posted by christooss
Do a sudo -rf /etc/CPAN/config.*
and sudo -rf .cpan

Thank you.  I tried both commands and recieved the following:

```
sudo: illegal option `-rf'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
christian@linuxmain:~$ sudo -rf .cpan
sudo: please use single character options
sudo: illegal option `-rf'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

Any suggestions?  Sorry for being such a noob.

---

### Post by christooss on 2005-09-26
uppss sori

```
sudo rm -rf /etc/CPAN/config.*
sudo rm -rf .cpan
```

Do you notice a rm after sudo!!! It was a typo. Sprry again

---

### Post by cwhitmore75 on 2005-09-26
Perfect.  Worked without a hitch.  Thank you sooo much! :D

---

### Post by majikstreet on 2005-09-26
[QUOTE=arnieboy]
**Please NOTE: I have just installed Breezy (fresh installation) and I have installed gmail checker and its working flawlessly. Read this post again and follow it to make this work on a fresh Breezy installation**[/QUOTE]
I can confirm this. I read these instructions before you updated and it installed fine for me... I can say that gmailchecker ROCKS!

---

### Post by Dooglus on 2005-09-26
I found a much easier way to install this, using existing ubuntu packages rather than all that CPAN stuff.  It means you don't need to install any build tools or compile anything, and the only stuff you need to install as root are official ubuntu packages.  I run breezy, so I can't say whether this will work on hoary or not.  Please let me know if I missed anything here - if so, I'll correct it.

In the following instructions, replace "/home/user" with any path you like.

Download the source for checkgmail from sourcefource, as before from```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.4.tar.bz2?download
```Save the file into /home/user.

cd to /home/user and extract the tar file, using```
tar xfj checkgmail-1.4.tar.bz2
```This will make a new directory called checkgmail-1.4 in the current directory.

Breezy is missing one of the Perl modules you need for some reason, so we'll need to get it from CPAN.  We can store it locally, however, like this:```
cd /home/user/checkgmail-1.4 && mkdir Crypt && wget -O Crypt/Simple.pm http://search.cpan.org/src/KASEI/Crypt-Simple-0.06/Simple.pm
```

We need to tell the checkgmail script where to find our local copy of Simple.pm:
cd to /home/user/checkgmail-1.4 and edit the "checkgmail" script to make the first line say```
#!/usr/bin/perl -w -I/home/user/checkgmail-1.4
```

Then all you need to do is ```
sudo apt-get install libwww-perl libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl libfreezethaw-perl libgtk2-trayicon-perl libxml-simple-perl
```and you're done.  To run the checker, just run```
/home/user/checkgmail-1.4/checkgmail
```

---

### Post by hugin0 on 2005-11-10
i'm having major difficulties with XML::Simple.  i can't seem to get it installed either with apt or CPAN.  it gives me errors from the XML::SAX package, but that installed perfectly fine.

anyone else having this difficulty??


/jhs

---

### Post by lynng on 2005-12-09
I followed the first post of this howto, and I have checkgmail running nicely.  However, I am having trouble installing packages from the repositories.  I'm getting errors like this:
```
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not installed.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Setting up libsdl-image1.2 (1.2.4-1) ...

Setting up libsdl-console (1.3-3) ...

Setting up libsdl-gfx1.2 (2.0.9-4) ...

Setting up libsdl-mixer1.2 (1.2.6-1.1) ...

Setting up libsdl-net1.2 (1.2.5-3) ...

Setting up libsdl-ttf2.0-0 (2.0.6-5) ...

Setting up libsdl-perl (1.20.3-1ubuntu7) ...
Setting up fb-music-high (0.1.1) ...
Setting up frozen-bubble-data (1.0.0-6) ...
Setting up frozen-bubble (1.0.0-6) ...

Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I think this could be related to all the MCPAN stuff I did to get checkgmail working.  Is there a way to reverse all of that?

---

### Post by Mguel on 2005-12-14
[QUOTE=lynng]I followed the first post of this howto, and I have checkgmail running nicely.  However, I am having trouble installing packages from the repositories.  I'm getting errors like this:[/QUOTE]

I'm getting the same error on the terminal when trying to install anything, with the following error message:

```
E: libxml-sax-perl: subprocess post-installation script returned error exit status 255
E: libxml-libxml-perl: dependency problems - leaving unconfigured
E: libxml-simple-perl: dependency problems - leaving unconfigured
```

:(

Thanks in advance,
Mguel

---

### Post by cwhitmore75 on 2005-12-15
When entering the following command:

```
sudo perl -MCPAN -e 'install XML::Simple'
```

I get the following error:

```
christian@mainbox:~/checkgmail-1.3$ sudo perl -MCPAN -e 'install XML::Simple'
CPAN: Storable loaded ok
Going to read /home/christian/.cpan/Metadata
  Database was generated on Thu, 15 Dec 2005 10:06:21 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/christian/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.1 4.tar.gz ok
Scanning cache /home/christian/.cpan/build for sizes
XML-Simple-2.14/
XML-Simple-2.14/t/
XML-Simple-2.14/t/1_XMLin.xml
XML-Simple-2.14/t/lib/
XML-Simple-2.14/t/lib/TagsToUpper.pm
XML-Simple-2.14/t/6_ObjIntf.t
XML-Simple-2.14/t/1_XMLin.t
XML-Simple-2.14/t/srt.xml
XML-Simple-2.14/t/4_MemShare.t
XML-Simple-2.14/t/3_Storable.t
XML-Simple-2.14/t/7_SaxStuff.t
XML-Simple-2.14/t/A_XMLParser.t
XML-Simple-2.14/t/0_Config.t
XML-Simple-2.14/t/subdir/
XML-Simple-2.14/t/subdir/test2.xml
XML-Simple-2.14/t/2_XMLout.t
XML-Simple-2.14/t/5_MemCopy.t
XML-Simple-2.14/t/8_Namespaces.t
XML-Simple-2.14/t/test1.xml
XML-Simple-2.14/t/desertnet.src
XML-Simple-2.14/t/9_Strict.t
XML-Simple-2.14/Changes
XML-Simple-2.14/MANIFEST
XML-Simple-2.14/lib/
XML-Simple-2.14/lib/XML/
XML-Simple-2.14/lib/XML/Simple/
XML-Simple-2.14/lib/XML/Simple/FAQ.pod
XML-Simple-2.14/lib/XML/Simple.pm
XML-Simple-2.14/META.yml
XML-Simple-2.14/maketest
XML-Simple-2.14/README
XML-Simple-2.14/Makefile.PL
Removing previously used /home/christian/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

Checking installed modules ...
XML::SAX is installed, it will be used by the test suite
Checking if your kit is complete...
Looks good
Writing Makefile for XML::Simple
cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/ local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........ok 16/122Unable to recognise encoding of this document at /usr /local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/sha re/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/l ocal/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

```

Any suggestions?  The results of proceeding after this step is a binary that does nothing when you double click it.  It wont run from terminal either.

Thanks in advance.

---

### Post by christooss on 2005-12-15
> won't install without force

Use Force. May the force of the hammer be with you :)

Sorry :(

---

### Post by arnieboy on 2005-12-15
guys plz use the updated howto in the breezy forums. (for breezy). this one's obsolete for breezy.

---

### Post by pvgorp on 2006-02-15
The install command for XML::Simple gives me the following error:

t/9_Strict........ok 2/38Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok                                                         
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force


How can I fix this?  I don't know anything about the PERL build details so I haven't tried the 'force' way yet...

Thanks in advance,
Pieter.

---

### Post by duckboy on 2006-02-18
Is there an alternative to rebooting as the last step in order to use the notifier? I just hate to reboot in Linux :)

---

### Post by christooss on 2006-02-18
> now a folder called checkgmail-1.3 will be created in your home folder and inside it will be the checkgmail perl binary which u need to add to system-->preferences-->sessions-->startup programs
The path of the executable would be /home/user_name/checkgmail-1.3/checkgmail
U can also open a nautilus window and double click on /home/user_name/checkgmail-1.3/checkgmail to make it run (or run it from terminal). next time u boot in to GNOME it will start automatically and u will see how nifty and unobtrusive it is.

You probably think this as the last step. There is no need to reboot. You can also open a nautilus window and double click on /home/user_name/checkgmail-1.3/checkgmail

---

### Post by duckboy on 2006-02-18
when I try to run checkgmail-1.3/checkgmail  nothing happens?

---

### Post by tntc1978 on 2006-02-20
How do I undo these steps? I would like to unistall the entire proces.

```
sudo perl -MCPAN -e 'install Bundle::LWP' 
sudo perl -MCPAN -e 'install Crypt::Simple' 
sudo perl -MCPAN -e 'install XML::Simple' 
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```

---

### Post by reiki on 2006-02-23
OK I was having the same kind of problem with libxml-sax-perl.
It threw errors when I tried to install other stuff. Complained about libxml-sax-perl exiting with an error code and libxml-libxml-perl not being configured and dependancy problems... I was freaking.

Now I think SOME people have problems and some don't maybe depending on where you picked up your files from for this installation. Here's what I found...

libxml-libxml-perl depends on libxml-sax-perl which is currently "broken" so to speak, at least it didn't install properly during my installation.

the problem is that libxml-sax-perl installs two different version of the XML::SAX Lib with two different files located here :

/usr/local/share/perl/5.8.7/XML/SAX.pm
/usr/share/perl5/XML/SAX.pm

once the package is extracted it does its post install thing and calls the script update-perl-sax-parsers. That perl script loads the XML::SAX and tries to call a debian specific function. The class loaded is from the first file above which does not have that debian function so the script execution fails and the apt process returns with error and stops any further package installation..

the very simple way to get around that problem is to overwrite the fist SAX.pm file located in /usr/local/share/perl/5.8.7/XML/SAX.pm with the second one /usr/share/perl5/XML/SAX.pm

Do this:
```

sudo cp /usr/share/perl5/XML/SAX.pm /usr/local/share/perl/5.8.7/XML/SAX.pm
```

In my case the original install failed in such a way that /usr/local/share/perl/5.8.7/XML/SAX.pm was not even there.

You'll overwrite the first SAX.pm file (or simply copy one into place) as explained above and then try to install libxml-libxml-perl again ( sudo apt-get install libxml-libxml-perl) and now everything should go smoothly..

once libxml-libxml-perl is installed you're good to go

---

### Post by arnieboy on 2006-02-23
**I am rewriting the 2 key steps in this howto. **
Poofy: please make necessary revisions in the first post:
```
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev make manpages-dev autoconf automake1.9 libtool flex bison gcc libxml-simple-perl libcrypt-ssleay-perl
```

```
sudo perl -MCPAN -e 'install Bundle::LWP'
sudo perl -MCPAN -e 'install Crypt::Simple'
```

---

### Post by arnieboy on 2006-02-23
CPAN does not support uninstallation. Hence installation of perl modules through CPAN need to be kept to a minimum. In the near future, we will have deb packages for all perl modules.

---

### Post by tntc1978 on 2006-03-01
#118 Reiki, I'm sorry, but I didn't see your responce. I just made a fresh install of the Ubuntu installation. But now you have given others tha answers. Thanks a bunch

---

### Post by TeeAhr1 on 2006-03-30
Hey, trying to install the new version here (1.7.1).  I get through the howto up to **sudo perl -MCPAN -e 'install XML::Simple'**, then I get this:

```
CPAN: Storable loaded ok
Going to read /home/teeahr1/.cpan/Metadata
  Database was generated on Wed, 29 Mar 2006 15:44:03 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/teeahr1/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz ok
Scanning cache /home/teeahr1/.cpan/build for sizes
XML-Simple-2.14/
XML-Simple-2.14/t/
XML-Simple-2.14/t/1_XMLin.xml
XML-Simple-2.14/t/lib/
XML-Simple-2.14/t/lib/TagsToUpper.pm
XML-Simple-2.14/t/6_ObjIntf.t
XML-Simple-2.14/t/1_XMLin.t
XML-Simple-2.14/t/srt.xml
XML-Simple-2.14/t/4_MemShare.t
XML-Simple-2.14/t/3_Storable.t
XML-Simple-2.14/t/7_SaxStuff.t
XML-Simple-2.14/t/A_XMLParser.t
XML-Simple-2.14/t/0_Config.t
XML-Simple-2.14/t/subdir/
XML-Simple-2.14/t/subdir/test2.xml
XML-Simple-2.14/t/2_XMLout.t
XML-Simple-2.14/t/5_MemCopy.t
XML-Simple-2.14/t/8_Namespaces.t
XML-Simple-2.14/t/test1.xml
XML-Simple-2.14/t/desertnet.src
XML-Simple-2.14/t/9_Strict.t
XML-Simple-2.14/Changes
XML-Simple-2.14/MANIFEST
XML-Simple-2.14/lib/
XML-Simple-2.14/lib/XML/
XML-Simple-2.14/lib/XML/Simple/
XML-Simple-2.14/lib/XML/Simple/FAQ.pod
XML-Simple-2.14/lib/XML/Simple.pm
XML-Simple-2.14/META.yml
XML-Simple-2.14/maketest
XML-Simple-2.14/README
XML-Simple-2.14/Makefile.PL
Removing previously used /home/teeahr1/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

Checking installed modules ...
XML::SAX is installed, it will be used by the test suite
Checking if your kit is complete...
Looks good
Writing Makefile for XML::Simple
cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........ok 6/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........ok 24/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........ok 66/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 187/196Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
```

I know the new version is pretty fresh, so I don't know if anyone's had a chance to test it out, but any help would be appreciated.  Thx!
-pete

---

### Post by BobSongs on 2006-05-15
I'll tell y'all what I did to get my GMail notifier working. It's not going to be simple tutorial style. So, if someone wants to thicken it, go ahead.

1. Head to [http://search.cpan.org/](http://search.cpan.org/)
2. Search for each of the following and download each (copy and paste each line exactly as detailed below):
[INDENT]Bundle::LWP
Crypt::Simple
XML::Simple
Crypt::SSLeay[/INDENT]
3. Double click each file and copy the folder in the archive to some favorite location.
4. In the terminal cd your way to each folder in the order above and do the following: 
```
sudo perl Makefile.PL
make
make test
sudo make install
```
5. Then download a recent copy of GMail Notifier from [http://prdownloads.sourceforge.net/checkgmail/](http://prdownloads.sourceforge.net/checkgmail/)
6. Follow the instructions in this tutorial (Page 1) as to what to do with this file.

I just did it and the GMail notifier works just fine.

:)

---

### Post by christooss on 2006-05-15
[http://ubuntuforums.org/showpost.php?p=372215&postcount=106](http://ubuntuforums.org/showpost.php?p=372215&postcount=106)

I think that howto in this link is simplier :)

---

### Post by frodon on 2006-06-05
Does this guide works for dapper ?

---

### Post by bluenova on 2006-06-05
[QUOTE=frodon]Does this guide works for dapper ?[/QUOTE]
Why not just:

sudo apt-get install gmail-notify

?

---

### Post by frodon on 2006-06-05
[QUOTE=bluenova]Why not just:

sudo apt-get install gmail-notify

?[/QUOTE]Because i don't use gmail and checkgmail ;), i just wanted to archive this guide in the UDSF but i found what i was looking for now (some instructions which works for dapper)

Thanks anyway

---

### Post by bluenova on 2006-06-05
[QUOTE=frodon]Because i don't use gmail and checkgmail ;), i just wanted to archive this guide in the UDSF but i found what i was looking for now (some instructions which works for dapper)

Thanks anyway[/QUOTE]
Ah sorry, I would say it's obsoleted as the gmail-notify is now in the repos.

---

### Post by vvlist on 2006-06-05
I've been using CheckGmail for awhile now, absolutely love it's simplicity. I'm using 1.9 now, and it allows you to delete new mail without opening a browser, amazing! I can't believe this great progam isn't in the repos... It requires a mess of -dev packages, but so worth it.

---

### Post by marcog on 2006-06-22
I went through quite a lot to try installing checkgmail, manualling installing all the required modules. I now get a seg fault!! Any ideas?

PS: I'm running dapper

---

### Post by pywye on 2006-06-28
Bonjour
J obtiens ceci lorsque je lance la commande suivante:
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev make manpages-dev autoconf automake1.9 libtool flex bison gcc

Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet ncftp

Voila je suis un chti newbi donc je ne vois pas trop quoi faire..

---

### Post by pywye on 2006-06-28
Sorry thought it was in french but the problem is still the same
Tryied everything but I can t seem to get this perl trayicon installed...

---

### Post by bluenova on 2006-06-28
[QUOTE=pywye]Sorry thought it was in french but the problem is still the same
Tryied everything but I can t seem to get this perl trayicon installed...[/QUOTE]
What's wrong with using the one in the repos?

sudo apt-get install gmail-notify

---

### Post by pywye on 2006-07-01
[QUOTE=pywye]Sorry thought it was in french but the problem is still the same
Tryied everything but I can t seem to get this perl trayicon installed...[/QUOTE]

Okay great I am all done... I am a newbie :KS how cute :) , and I know this may be a bit funny, but my problem was that I didn't have the "universe multiverse " in my sources.list

On a fresh install, when you're a newbie, it's not the first thing you do... You just care about installing the stuff you need and do not think of this trouble...

Do you know where I could notice this for other new users not to be tricked ?

Thanks.
PS:Sorry about the english, not enough coffee this morning, to much other drinks yesterday :)O:)

---

### Post by s_h_a_d_o_w_s on 2006-07-05
au moins je t'ai compris :-)

---

### Post by Dubbel on 2006-07-10
> **bluenova said:**
> What's wrong with using the one in the repos?

sudo apt-get install gmail-notify
Does this also work with multiple gmail-accounts ?

---

### Post by s_h_a_d_o_w_s on 2006-07-13
I can't get it to play my .wav file when I get an e-mail /

---

### Post by xinix on 2006-07-13
My only problem with gmail-notify is that it keeps your password in plaintext in your home folder.  Not sure I want to make my email password so easy to find.

---

### Post by rasmusbp on 2006-07-18
I've encountered a strange problem using gmailchecker, and after some googling without finding a solution, I'll try this forum. I followed this excellent HOWTO guide and everything worked fine in the beginning. Now when I open ubuntu, the login screen pops up every time and asks for both username and password (despite the fact that I've configured to remember the pw) - and it keeps telling me "incorrect username" (and I've tried ten times now, I'm definitely using the right username and password). Any ideas on what might be causing this?

Thanks!

Breast wishes, 
Rasmus

---

### Post by waveslider on 2006-08-23
After installing checkgmail, I right-clicked on the icon on my panel, and then accidentally clicked "Remove from panel". 

Please pardon my ignorance, but I'm really new to linux & Ubuntu. Can anyone tell me how I can get the notification tray icon back?

Thanks

---

### Post by frenzie on 2006-08-24
> **arnieboy said:**
> did u get this error when u tried to do:
```
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```?

Hi, a bit of a reshash, but im having trouble installing Crypt::SSLeay also :(

Istalled:
shanna@shantaram:/usr/include$ sudo apt-get install openssl libssl-dev
Reading package lists... Done
Building dependency tree... Done
openssl is already the newest version.
libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Problem:
shanna@shantaram:~$ sudo perl -MCPAN -e 'install Crypt::SSLeay'
CPAN: Storable loaded ok
Going to read /home/shanna/.cpan/Metadata
  Database was generated on Wed, 23 Aug 2006 22:33:13 GMT
Running install for module Crypt::SSLeay
Running make for C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/shanna/.cpan/sources/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz ok
Scanning cache /home/shanna/.cpan/build for sizes
Crypt-SSLeay-0.51/
Crypt-SSLeay-0.51/t/
Crypt-SSLeay-0.51/t/net_ssl.t
Crypt-SSLeay-0.51/t/ssl_context.t
Crypt-SSLeay-0.51/lib/
Crypt-SSLeay-0.51/lib/Crypt/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/MainContext.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Conn.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/X509.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Err.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/CTX.pm
Crypt-SSLeay-0.51/lib/Net/
Crypt-SSLeay-0.51/lib/Net/SSL.pm
Crypt-SSLeay-0.51/certs/
Crypt-SSLeay-0.51/certs/ca-bundle.crt
Crypt-SSLeay-0.51/certs/notacakeynopass.pem
Crypt-SSLeay-0.51/certs/notacacert.pem
Crypt-SSLeay-0.51/MANIFEST
Crypt-SSLeay-0.51/typemap
Crypt-SSLeay-0.51/MANIFEST.SKIP
Crypt-SSLeay-0.51/SSLeay.pm
Crypt-SSLeay-0.51/CHANGES
Crypt-SSLeay-0.51/lwp-ssl-test
Crypt-SSLeay-0.51/net_ssl_test
Crypt-SSLeay-0.51/SSLeay.xs
Crypt-SSLeay-0.51/README
Crypt-SSLeay-0.51/Makefile.PL
Removing previously used /home/shanna/.cpan/build/Crypt-SSLeay-0.51

  CPAN.pm: Going to build C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz

Found OpenSSL (version OpenSSL 0.9.8) installed at /usr
Which OpenSSL build path do you want to link against? [/usr]

================================================
BUILD INFORMATION
================================================

ssl dir:        /usr
libraries:      -lssl -lcrypto -lgcc -lRSAglue -lrsaref
include dir:    /usr/include
ssl header:     openssl/ssl.h
ssl candidate:  /usr; /usr/include/openssl; OpenSSL 0.9.8

================================================

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgcc
Note (probably harmless): No library found for -lRSAglue
Note (probably harmless): No library found for -lrsaref
Writing Makefile for Crypt::SSLeay
cp lib/Crypt/SSLeay/X509.pm blib/lib/Crypt/SSLeay/X509.pm
cp lib/Net/SSL.pm blib/lib/Net/SSL.pm
cp SSLeay.pm blib/lib/Crypt/SSLeay.pm
cp lib/Crypt/SSLeay/MainContext.pm blib/lib/Crypt/SSLeay/MainContext.pm
cp lib/Crypt/SSLeay/Conn.pm blib/lib/Crypt/SSLeay/Conn.pm
cp lib/Crypt/SSLeay/CTX.pm blib/lib/Crypt/SSLeay/CTX.pm
cp lib/Crypt/SSLeay/Err.pm blib/lib/Crypt/SSLeay/Err.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  SSLeay.xs > SSLeay.xsc && mv SSLeay.xsc SSLeay.c
cc -c  -I/usr/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"   SSLeay.c
SSLeay.xs: In function ‘XS_Crypt__SSLeay__Conn_new’:
SSLeay.xs:252: warning: passing argument 2 of ‘SSL_set_info_callback’ from incompatible pointer type
Running Mkbootstrap for Crypt::SSLeay ()
chmod 644 SSLeay.bs
rm -f blib/arch/auto/Crypt/SSLeay/SSLeay.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib SSLeay.o  -o blib/arch/auto/Crypt/SSLeay/SSLeay.so   -L/usr/lib -lssl -lcrypto
chmod 755 blib/arch/auto/Crypt/SSLeay/SSLeay.so
cp SSLeay.bs blib/arch/auto/Crypt/SSLeay/SSLeay.bs
chmod 644 blib/arch/auto/Crypt/SSLeay/SSLeay.bs
Manifying blib/man3/Crypt::SSLeay.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/net_ssl........dubious
        Test returned status 0 (wstat 11, 0xb)
t/ssl_context....dubious
        Test returned status 0 (wstat 11, 0xb)
FAILED--2 test scripts could be run, alas--no output ever seen
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force


Any ideas on what the error could be now? It is apparently happy finding the openssl now, but still fails :/

---

### Post by bungaknotty on 2006-08-24
Hi im struggling with the first line here can someone please help me. I am running dapper drake

this is my error:

jerry@jerry-desktop:~$ sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev gcc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ncftp

---

### Post by christooss on 2006-08-24
no need for compiling. there are ubuntu repositories avalible on official page

---

### Post by bajjer31 on 2006-09-01
> **christooss said:**
> no need for compiling. there are ubuntu repositories avalible on official page

I hate to keep going over this...but I too have had problems. I tried through the howto, had some problems with the last MCPAN steps, but seemed to get everyting installed.  Checkgmail gets a segmentation fault. I've also installed via the repositories, and it installs just fine, but still the segmentation fault.  I don't suppose anyone has any ideas on how to get this to work short of a system restore?  
```

Setting up checkgmail (1.9.3-0ubuntu1) ...
///
bill@topperexpress:~$ checkgmail
Segmentation fault
```

Thanks in advance (I believe this is my first post, though I've used Ubuntu for quite awhile...switched from FC1,2,3,etc.) :) 

Bill

****Edit See below for fix:

---

### Post by bajjer31 on 2006-09-01
Edit, I found the fix!  From the checkgmail site:
> If CheckGmail segfaults ....
This isn't anything to do with CheckGmail, but a bug in the Crypt-SSLeay package when used with OpenSSL 0.9.8 or later. Some distros, notably Ubuntu, have already patched the Crypt::SSLeay module to fix this bug and hopefully most will soon follow.

However, if you are building the module from CPAN or otherwise encounter this error, you can use a quick fix kindly provided by Alex Shurupov:

Issue the following "sed" command (after unpacking the Crypt::SSLeay tarball and changing directories into the root of the source tree) to fix the problem:
```

sed -i '/algorithms/ a\ SSL_library_init();' SSLeay.xs
```

I downladed the Crypt::SSLeay source, unpacked it, issued the sed command, then just recompiled it.  After this, checkgmail worked just fine.

Thanks,
Bill

---

### Post by chris.olsen on 2006-10-28
For some reason it just hangs when I run the command
sudo perl -MCPAN -e 'install Bundle::LWP'

It seems that it is unable to retrieve the file, although I have downloaded the file directly with no problems.

Any advice?  

BTW I am using Dapper

====
chris@ubuntu:~$ sudo perl -MCPAN -e 'install Bundle::LWP'
CPAN: Storable loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)

---

### Post by christooss on 2006-10-28
There are deb packages

---

### Post by keka on 2006-11-15
Hi, I really like this feature that you provided, but I am unable to install SSleay. 
After I run "sudo perl -MCPAN -e 'install Crypt::SSLeay'" it asks me this: Found OpenSSL (version OpenSSL 0.9.8) installed at /usr
Which OpenSSL build path do you want to link against? [/usr] 


I hit enter and get this message: 
================================================
BUILD INFORMATION
================================================

ssl dir:        /usr
libraries:      -lssl -lcrypto -lgcc -lRSAglue -lrsaref
include dir:    /usr/include
ssl header:     openssl/ssl.h
ssl candidate:  /usr; /usr/include/openssl; OpenSSL 0.9.8

================================================

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgcc
Note (probably harmless): No library found for -lRSAglue
Note (probably harmless): No library found for -lrsaref
Writing Makefile for Crypt::SSLeay
cp lib/Crypt/SSLeay/X509.pm blib/lib/Crypt/SSLeay/X509.pm
cp lib/Net/SSL.pm blib/lib/Net/SSL.pm
cp SSLeay.pm blib/lib/Crypt/SSLeay.pm
cp lib/Crypt/SSLeay/MainContext.pm blib/lib/Crypt/SSLeay/MainContext.pm
cp lib/Crypt/SSLeay/Conn.pm blib/lib/Crypt/SSLeay/Conn.pm
cp lib/Crypt/SSLeay/CTX.pm blib/lib/Crypt/SSLeay/CTX.pm
cp lib/Crypt/SSLeay/Err.pm blib/lib/Crypt/SSLeay/Err.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  SSLeay.xs > SSLeay.xsc && mv SSLeay.xsc SSLeay.c
cc -c  -I/usr/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"   SSLeay.c
SSLeay.xs: In function ‘XS_Crypt__SSLeay__Conn_new’:
SSLeay.xs:252: warning: passing argument 2 of ‘SSL_set_info_callback’ from incompatible pointer type
Running Mkbootstrap for Crypt::SSLeay ()
chmod 644 SSLeay.bs
rm -f blib/arch/auto/Crypt/SSLeay/SSLeay.so
cc  -shared -L/usr/local/lib SSLeay.o  -o blib/arch/auto/Crypt/SSLeay/SSLeay.so \
           -L/usr/lib -lssl -lcrypto    \
          
chmod 755 blib/arch/auto/Crypt/SSLeay/SSLeay.so
cp SSLeay.bs blib/arch/auto/Crypt/SSLeay/SSLeay.bs
chmod 644 blib/arch/auto/Crypt/SSLeay/SSLeay.bs
Manifying blib/man3/Crypt::SSLeay.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/net_ssl........dubious                                                     
        Test returned status 0 (wstat 139, 0x8b)
t/ssl_context....dubious                                                     
        Test returned status 0 (wstat 139, 0x8b)
FAILED--2 test scripts could be run, alas--no output ever seen
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
--------------------------------

Please help me get through this, thanks

---

### Post by keka on 2006-11-15
Sorry for the long question. I ran into this: 


-----------
apt-get install checkgmail
-----------

After that everything worked ! thanks

---

### Post by arnieboy on 2006-11-15
This howto is way outdated. Please move to jail.
Thanks.
-Arnie

---

### Post by kiikkuja on 2006-12-18
Can someone help me with my problem? I run Kubuntu 6.10 and installed checkgmail through
repos. The program reports that i have mail, but i cannot read the mail with it. I used to have it installed in my dapper/GNOME and it opened my gmail account through firefox. What to do?

---

### Post by bokibre on 2006-12-24
Is there any solution for checkgmail fully working with beryl, when beryl is working i can't archive mark as read ... from chekgmail... on author homepage i found this:

CheckGmail and XGL/Compiz
Sorry, but these two don't seem to like each other very much (CheckGmail still works, but you won't be able to use a lot of the nifty features). I don't have a system running XGL and can't bugfix this one myself, but from what I can tell the issue lies with incompatibilities in the Gtk2-perl modules (and more specifically the signal_connect methods) rather than my own code. Please stop reporting this issue!! At the moment there's nothing I can do about it, and anyone experiencing this problem would be better off reporting it to the Gtk2-perl developers. Thanks! :)

---

### Post by monica_ska on 2007-06-04
Hi all,

I have been trying to install it following this how-to but I get this error:

Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/share/perl5/LWP/Protocol.pm line 114.

Do you know what it is?

---

