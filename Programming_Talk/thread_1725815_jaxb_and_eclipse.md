---
title: "jaxb and eclipse"
date: 2011-04-10
forum: Programming Talk
---

### Post by Segaman on 2011-04-10
Guys who can provide a repository link for installing jaxb tools for eclipse? 
Cause I`ve downloaded jwsdp-2.0  and when I`m runnig this script I got errors:
```
Using /var/tmp as temporary directory...
Searching for Java(TM) 2 Platform, Standard Edition...
tail: &#1085;&#1077; &#1074;&#1076;&#1072;&#1108;&#1090;&#1100;&#1089;&#1103; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; `+368' &#1076;&#1083;&#1103; &#1095;&#1080;&#1090;&#1072;&#1085;&#1085;&#1103;: No such file or directory
Initializing InstallShield Wizard...
Exception in thread "main" java.lang.NoClassDefFoundError: JWSDP
Caused by: java.lang.ClassNotFoundException: JWSDP
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: JWSDP. Program will exit.
```

But then I used ```
 [I]export  _POSIX2_VERSION=199209
```

which gives me ```
 he wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
```

Please help!
Thanks.
[/I]

---

