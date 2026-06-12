---
title: "Java application does not work anymore"
date: 2021-05-22
forum: New to Ubuntu
---

### Post by maketopsite on 2021-05-22
```

Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-11-openjdk-amd64/lib/libawt_xawt.so
    at java.base/java.lang.ClassLoader.loadLibrary(ClassLoader.java:2630)
    at java.base/java.lang.Runtime.load0(Runtime.java:768)
    at java.base/java.lang.System.load(System.java:1837)
    at java.base/java.lang.ClassLoader$NativeLibrary.load0(Native Method)
    at java.base/java.lang.ClassLoader$NativeLibrary.load(ClassLoader.java:2442)
    at java.base/java.lang.ClassLoader$NativeLibrary.loadLibrary(ClassLoader.java:2498)
    at java.base/java.lang.ClassLoader.loadLibrary0(ClassLoader.java:2694)
    at java.base/java.lang.ClassLoader.loadLibrary(ClassLoader.java:2648)
    at java.base/java.lang.Runtime.loadLibrary0(Runtime.java:830)
    at java.base/java.lang.System.loadLibrary(System.java:1873)
    at java.desktop/java.awt.Toolkit$3.run(Toolkit.java:1399)
    at java.desktop/java.awt.Toolkit$3.run(Toolkit.java:1397)
    at java.base/java.security.AccessController.doPrivileged(Native Method)
    at java.desktop/java.awt.Toolkit.loadLibraries(Toolkit.java:1396)
    at java.desktop/java.awt.Toolkit.<clinit>(Toolkit.java:1429)
    at java.desktop/java.awt.EventQueue.invokeLater(EventQueue.java:1312)


```

source code line which caused error:
```
    public static void main(String[] args) {
**        EventQueue.invokeLater(new Runnable() {**
            public void run() {


```

I don't remember to encounter such error before.
Ubuntu 20.04

Any idea please ?

---

### Post by TheFu on 2021-05-22
Not many Java devs here. Best to ask programming questions on a Java programming forum.  
The first line says that  /usr/lib/jvm/java-11-openjdk-amd64/lib/libawt_xawt.so can't be opened.
Did you check whether it exists? 
If it does not exist on the system, you'll need to find the package which includes that shared library.

---

### Post by maketopsite on 2021-05-23
> **TheFu said:**
> Not many Java devs here. Best to ask programming questions on a Java programming forum.  
The first line says that  /usr/lib/jvm/java-11-openjdk-amd64/lib/libawt_xawt.so can't be opened.
Did you check whether it exists? 
If it does not exist on the system, you'll need to find the package which includes that shared library.

Thank you. This has solved the issue:
```
apt-get install  openjdk-11-jre
```

---

