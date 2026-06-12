---
title: "Can anyone help me with a Java error?"
date: 2006-11-01
forum: Programming Talk
---

### Post by HedonismBot on 2006-11-01
Running ubuntu 6.10 on new server. Old server ran supplied app just fine, new one, not so good ](*,) 

This is the error text returned to me by JVM:

Exception in thread "main" java.lang.NoClassDefFoundError: internetclient/InternetClient
   at _ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.5.0.0)
   at _ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.5.0.0)
   at _ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.5.0.0)
   at _ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.5.0.0)
   at _ZN4java4lang12LinkageErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.5.0.0)
   at _ZN4java4lang20NoClassDefFoundErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.5.0.0)
   at _ZN3gnu3gcj7runtime11FirstThread3runEv (/usr/lib/libgcj.so.5.0.0)
   at _Z13_Jv_ThreadRunPN4java4lang6ThreadE (/usr/lib/libgcj.so.5.0.0)
   at _Z11_Jv_RunMainPN4java4lang5ClassEPKciPS4_b (/usr/lib/libgcj.so.5.0.0)
   at __gcj_personality_v0 (/usr/sbin/sportsticker/java.version=1.4.2)
   at __libc_start_main (/lib/tls/libc-2.3.4.so)
   at _Jv_RegisterClasses (/usr/sbin/sportsticker/java.version=1.4.2)


I'm not a java programmer, Just a sysadmin...can anyone point me in the right direction??? :D

Thanks!

---

### Post by meng on 2006-11-01
Looks like this is trying to use the open-source java, not Sun's Java - do you need Sun's java? If so, download and install and set it as the default java by following these instructions:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by johnnymac on 2006-11-02
Yup - that server is using the gjc...YUK!  You need to use the one from Sun.

---

