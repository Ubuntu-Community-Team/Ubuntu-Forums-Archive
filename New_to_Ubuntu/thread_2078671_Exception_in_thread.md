---
title: "Exception in thread"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by alnovaisd on 2012-10-31
Hey guys,

I have a problem to install a software, when  I enter the comand "./instalar.sh" it retorn:

```
andre@andre-Aspire-4739:~/Documentos/jcompany$ ./instalar.sh 
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/andre/Documentos/jcompany/jre/lib/i386/xawt/libmawt.so: libXtst.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
    at java.lang.Runtime.load0(Runtime.java:770)
    at java.lang.System.load(System.java:1005)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1030)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1594)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1616)
    at java.awt.Color.<clinit>(Color.java:263)
    at com.izforge.izpack.installer.InstallData.<init>(InstallData.java:51)
    at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:107)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
    at java.lang.Class.newInstance0(Class.java:355)
    at java.lang.Class.newInstance(Class.java:308)
    at com.izforge.izpack.installer.Installer.main(Installer.java:62)

```My OS is ubuntu 12.10 64 bits, and I try to install a software that's 32 bits.

Someone can help me?

thanks

---

### Post by coffeecat on 2012-10-31
Not a Forum Feedback and Help thread.

*Thread moved to **Absolute Beginners Section**.*

---

### Post by drmrgd on 2012-10-31
Possibly need to install libxt6 and / or libxt-java?  Try:

```
sudo apt-get install libxt-java libxt6
```

---

