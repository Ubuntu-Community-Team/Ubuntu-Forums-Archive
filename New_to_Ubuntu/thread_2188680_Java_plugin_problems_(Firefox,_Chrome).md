---
title: "Java plugin problems (Firefox, Chrome)"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by onebir on 2013-11-18
I followed I think amounted to "The Hard Way" instructions here (it was a while ago):
[http://www.maketecheasier.com/install-java-runtime-in-ubuntu](http://www.maketecheasier.com/install-java-runtime-in-ubuntu)

Everything seems in order:

```
bir@N2C:~/.mozilla/plugins$ java -versionjava version "1.7.0_40"
Java(TM) SE Runtime Environment (build 1.7.0_40-b43)
Java HotSpot(TM) Server VM (build 24.0-b56, mixed mode)
bir@N2C:~/.mozilla/plugins$ ls -lh
total 100K
lrwxrwxrwx 1 bir bir  46 Nov 18 18:41 libnpjp2.so -> /usr/java/jdk1.7.0_40/jre/lib/i386/libnpjp2.so
-rwxr-xr-x 1 bir bir 97K Oct 27 21:00 npatgpc.so
bir@N2C:~/.mozilla/plugins$ ls /usr/java/jdk1.7.0_40/jre/lib/i386/ |grep libnpjplibnpjp2.so
libnpjp2.so


```

However, in Firefox the Java test page tells me the plugin has crashed; Chrome starts the Icedtea7 plugin (also installed with OpenJDK, see below) but then nothing happens.

I'm using Xubuntu 13.04, with the following packages installed:
```
bir@N2C:~/.mozilla/plugins$ dpkg --get-selections |grep javaca-certificates-java                install
gir1.2-javascriptcoregtk-3.0            install
java-common                    install
libatk-wrapper-java                install
libatk-wrapper-java-jni:i386            install
libjavascriptcoregtk-1.0-0            install
libjavascriptcoregtk-3.0-0            install
tzdata-java                    install
bir@N2C:~/.mozilla/plugins$ dpkg --get-selections |grep tea
icedtea-7-jre-jamvm:i386            install
icedtea-7-plugin:i386                install
icedtea-netx:i386                install
icedtea-netx-common                install
bir@N2C:~/.mozilla/plugins$ dpkg --get-selections |grep jdk
jdk                        install
openjdk-7-jre:i386                install
openjdk-7-jre-headless:i386            install
openjdk-7-jre-lib                install

```

Update-alternatives:

```

ir@N2C:~/.mozilla/plugins$ sudo update-alternatives --config javac
There is 1 choice for the alternative javac (providing /usr/bin/javac).


  Selection    Path                                Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/jdk1.7.0_40/bin/javac   1         auto mode
* 1            /usr/lib/jvm/jdk1.7.0_40/bin/javac   1         manual mode


Press enter to keep the current choice
[*], or type selection number: 
bir@N2C:~/.mozilla/plugins$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).


  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1071      auto mode
  1            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1071      manual mode
* 2            /usr/lib/jvm/jdk1.7.0_40/bin/java               1         manual mode


Press enter to keep the current choice
[*], or type selection number: 

```

Any troubleshooting tips would be much appreciated; I seem to have run the gamut of what's out there on the web trying to get this working :s

---

### Post by dab5155 on 2014-02-10
I am having the same problem.  Were you ever able to find a solution?

---

