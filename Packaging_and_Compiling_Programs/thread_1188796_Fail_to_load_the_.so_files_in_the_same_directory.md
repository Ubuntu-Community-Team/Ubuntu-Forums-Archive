---
title: "Fail to load the *.so files in the same directory ?"
date: 2009-06-16
forum: Packaging and Compiling Programs
---

### Post by zgma1788 on 2009-06-16
Hi, everyone,

I am a beginner for linux programming.  I developped a consolo program "buildmysqldb" by QT, then find out the needed .so files by ldd command, then copy them (the orginnal so files and the symbol link files) together with my program. Now I copy all of them to another ubuntu computer, when I run "buildmysqldb", it is reported "cannot open shared object file"!  Why? Evenif I first run "> export PATH=$PATH:/opt/buildmysqldb-0.0.1
> export LD_LIBRARY_PATH=/opt/buildmysqldb-0.0.1:$LD_LIBRARY_PATH", the problem still remains. 
Please help me! 
The following is the screen shot (by webmin):

> cd /opt/buildmysqldb-0.0.1
> ls
buildmysqldb
day
libc-2.7.so
libcidn-2.7.so
libcidn.so.1
libcom_err.so.2
libcom_err.so.2.1
libcrypto.so.0.9.8
libc.so.6
libdl-2.7.so
libdl.so.2
libexpat.so.1
libexpat.so.1.5.2
libfontconfig.so.1
libfontconfig.so.1.3.0
libfreetype.so.6
libfreetype.so.6.3.16
libgcc_s.so.1
libgcrypt.so.11
libgcrypt.so.11.2.3
libglib-2.0.so.0
libglib-2.0.so.0.1600.6
libgnutls.so.13
libgnutls.so.13.9.1
libgpg-error.so.0
libgpg-error.so.0.3.0
libgssapi_krb5.so.2
libgssapi_krb5.so.2.2
libgthread-2.0.so.0
libgthread-2.0.so.0.1600.6
libk5crypto.so.3
libk5crypto.so.3.1
libkeyutils-1.2.so
libkeyutils.so.1
libkrb5.so.3
libkrb5.so.3.3
libkrb5support.so.0
libkrb5support.so.0.1
liblber-2.4.so.2
liblber-2.4.so.2.0.5
libldap_r-2.4.so.2
libldap_r-2.4.so.2.0.5
libm-2.7.so
libm.so.6
libmysqlclient_r.so.15
libmysqlclient_r.so.15.0.0
libnsl-2.7.so
libnsl.so.1
libpcre.so.3
libpcre.so.3.12.1
libpq.so.5
libpq.so.5.1
libpthread-2.7.so
libpthread.so.0
libQtCore.so.4
libQtCore.so.4.3.4
libQtNetwork.so.4
libQtNetwork.so.4.3.4
libQtSql.so.4
libQtSql.so.4.3.4
libresolv-2.7.so
libresolv.so.2
librt-2.7.so
librt.so.1
libsasl2.so.2
libsasl2.so.2.0.22
libsqlite3.so.0
libsqlite3.so.0.8.6
libsqlite.so.0
libsqlite.so.0.8.6
libssl.so.0.9.8
libstdc++.so.6
libstdc++.so.6.0.9
libtasn1.so.3
libtasn1.so.3.0.12
libz.so.1
libz.so.1.2.3.3
Uninstall buildmysqldb.desktop
> export PATH=$PATH:/opt/buildmysqldb-0.0.1
> export LD_LIBRARY_PATH=/opt/buildmysqldb-0.0.1:$LD_LIBRARY_PATH
> ./buildmysqldb
./buildmysqldb: error while loading shared libraries: libQtSql.so.4: cannot open shared object file: No such file or directory
> LD_LIBRARY_PATH=/opt/buildmysqldb-0.0.1:$LD_LIBRARY_PATH
> ./buildmysqldb
./buildmysqldb: error while loading shared libraries: libQtSql.so.4: cannot open shared object file: No such file or directory


Thanks in advence!

---

### Post by iponeverything on 2009-06-16
try LD_PATH

---

### Post by zgma1788 on 2009-06-16
I tried, still failed. 
**> export LD_PATH=/opt/buildmysqldb-0.0.1:$LD_PATH**
**> ./buildmysqldb**
./buildmysqldb: error while loading shared libraries: libQtSql.so.4: cannot open shared object file: No such file or directory
Thanks anyway!

---

### Post by zgma1788 on 2009-06-16
I found a way out:

Edit  /etc/ld.so.conf&#65292;add  /opt/buildmysqldb-0.0.1&#65292;
run ldconfig, then run ./buildmysqldb, it works!

---

