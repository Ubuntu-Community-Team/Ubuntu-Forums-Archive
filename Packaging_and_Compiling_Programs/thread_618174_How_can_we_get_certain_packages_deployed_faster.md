---
title: "How can we get certain packages deployed faster?"
date: 2007-11-20
forum: Packaging and Compiling Programs
---

### Post by mike503 on 2007-11-20
The current version of libgoogle-perftools0 and libgoogle-perftools-dev do not work on 7.10:

```
root@build01:~/build# LD_PRELOAD=/usr/lib/libtcmalloc.so ldd `which mysqld`
/bin/bash: symbol lookup error: /usr/lib/libtcmalloc.so: undefined symbol: pthread_key_create
root@build01:~/build#
```

Getting the latest directly from Google seems to work properly:

```
root@build01:~#  wget http://google-perftools.googlecode.com/files/libgoogle-perftools-dev_0.93-1_i386.deb
--02:09:24--  http://google-perftools.googlecode.com/files/libgoogle-perftools-dev_0.93-1_i386.deb
           => `libgoogle-perftools-dev_0.93-1_i386.deb'
Resolving google-perftools.googlecode.com... 72.14.253.82
Connecting to google-perftools.googlecode.com|72.14.253.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 429,018 (419K) [application/x-archive application/x-debian-package]

100%[====================================================================================>] 429,018        1.19M/s             

02:09:24 (1.18 MB/s) - `libgoogle-perftools-dev_0.93-1_i386.deb' saved [429018/429018]

root@build01:~# wget http://google-perftools.googlecode.com/files/libgoogle-perftools0_0.93-1_i386.deb
--02:09:37--  http://google-perftools.googlecode.com/files/libgoogle-perftools0_0.93-1_i386.deb
           => `libgoogle-perftools0_0.93-1_i386.deb'
Resolving google-perftools.googlecode.com... 72.14.253.82
Connecting to google-perftools.googlecode.com|72.14.253.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 156,892 (153K) [application/x-archive application/x-debian-package]

100%[====================================================================================>] 156,892       --.--K/s             

02:09:37 (1.25 MB/s) - `libgoogle-perftools0_0.93-1_i386.deb' saved [156892/156892]

root@build01:~# dpkg -i libgoogle-perftools-dev_0.93-1_i386.deb libgoogle-perftools0_0.93-1_i386.deb  
(Reading database ... 26797 files and directories currently installed.)
Preparing to replace libgoogle-perftools-dev 0.93-1 (using libgoogle-perftools-dev_0.93-1_i386.deb) ...
Unpacking replacement libgoogle-perftools-dev ...
Preparing to replace libgoogle-perftools0 0.8-5 (using libgoogle-perftools0_0.93-1_i386.deb) ...
Unpacking replacement libgoogle-perftools0 ...
Setting up libgoogle-perftools0 (0.93-1) ...
Setting up libgoogle-perftools-dev (0.93-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

root@build01:~# LD_PRELOAD=/usr/lib/libtcmalloc.so ldd `which mysqld`
        linux-gate.so.1 =>  (0xffffe000)
        /usr/lib/libtcmalloc.so (0xb7f9a000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7f8c000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f76000)
        libwrap.so.0 => /lib/libwrap.so.0 (0xb7f6e000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f6a000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f52000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7f24000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7f0c000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7e18000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7df3000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7de8000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c9e000)
        libstacktrace.so.0 => /usr/lib/libstacktrace.so.0 (0xb7c9c000)
        /lib/ld-linux.so.2 (0xb7fde000)
root@build01:~# 
```
Is there a process to getting this into the repositories faster? I really am trying to keep my installation in line with apt instead of installing and compiling my own stuff nowadays... I'd be fine with this normally except it doesn't work :)

Thanks in advance!

---

### Post by dholbach on 2007-11-21
If the source is available, [http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages) is the right way to get packages included.

---

