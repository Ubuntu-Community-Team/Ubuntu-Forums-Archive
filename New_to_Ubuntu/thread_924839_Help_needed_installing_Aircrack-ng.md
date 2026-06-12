---
title: "Help needed installing Aircrack-ng"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by manav_1001 on 2008-09-20
Hello all,

I am trying to install Aircrack-ng using the guide found [_here_]("http://aircrack-ng.org/doku.php?id=newbie_guide&DokuWiki=b2e6a9700921503fc44702092fb86eb7"). After downloading Aircrack-ng when I do "sudo make", I get the following errors:

[COLOR="Red"]make -C src all
make[1]: Entering directory `/home/manav/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/manav/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/manav/aircrack-ng-1.0-rc1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/manav/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/manav/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:4026: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:4026: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:4032: warning: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/manav/aircrack-ng-1.0-rc1/src'
make: *** [all] Error 2[/COLOR]

Can someone please tell me what am I doing wrong?
Thanks

---

### Post by Sorivenul on 2008-09-20
If you want to install from source, make sure you have build-essential installed:
```
sudo apt-get install build-essential

```
However, aircrack-ng is in the repository:
```
sudo apt-get install aircrack-ng
```

---

### Post by lswb on 2008-09-20
As Sorivenul said, it is available from the repositories using apt-get or synaptic.

If you must install from source, after untarring, did you look for a readme file? Very often there is a ./configure script that must be run before make. It's best to always check for any docs before running any commands.

---

### Post by manav_1001 on 2008-09-20
Thanks Sorivenul and lswb for ur replies. The code sudo apt-get install aircrack-ng didnt work, it gave me an error:
E: Couldn't find package aircrack-ng

However i got it installed from synaptic.

---

### Post by cusco on 2009-01-30
install libssl-dev package :-)

---

