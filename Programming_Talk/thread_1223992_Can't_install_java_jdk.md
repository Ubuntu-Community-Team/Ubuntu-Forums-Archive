---
title: "Can't install java jdk"
date: 2009-07-26
forum: Programming Talk
---

### Post by Majestic 888 on 2009-07-26
Okay well I'm trying to add java jdk on my vps and here is what I get

```
root@fatalms:~# apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate
```

---

### Post by philcamlin on 2009-07-26
The message you see about no installation candidate for sun-java6-plugin sounds like you run a 64-bit system.  Is that right?

There is no 64-bit Java plugin from Sun. You could try the icedtead-gcjwebplugin package, but you are correct that a lot of the banking applets don't work with it. I'd recommend taking a look in the 64-bit users forum, especially at the sticky. You might also try using Konquerer instead of Firefox.

Of course if you're not running a 64-bit system then there's something else to figure out.

Also, if you're still getting error messages about the sun-java6-doc package then just delete or purge it. It's not a normal package and you very likely don't care about it anyway.

---

### Post by Majestic 888 on 2009-07-26
Yea I'm running on a 64-bit system.
Well thanks for your help:)
I will try to find a way to get java on my system.

---

### Post by slavik on 2009-07-26
> **philcamlin said:**
> The message you see about no installation candidate for sun-java6-plugin sounds like you run a 64-bit system.  Is that right?

There is no 64-bit Java plugin from Sun. You could try the icedtead-gcjwebplugin package, but you are correct that a lot of the banking applets don't work with it. I'd recommend taking a look in the 64-bit users forum, especially at the sticky. You might also try using Konquerer instead of Firefox.

Of course if you're not running a 64-bit system then there's something else to figure out.

Also, if you're still getting error messages about the sun-java6-doc package then just delete or purge it. It's not a normal package and you very likely don't care about it anyway.
please check your sources. 64bit plugin has been available since update 12.

```

libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes

slavik@slavik-desktop:~$ file /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not stripped
slavik@slavik-desktop:~$ 

```

EDIT:
```

slavik@slavik-desktop:~$ apt-cache search sun java6 jdk
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
slavik@slavik-desktop:~$ 

```

What repositories do you have enabled? also, try doing a sudo apt-get update.

---

### Post by credobyte on 2009-07-27
```
sudo aptitude search sun-java6

```

Should give you a nice list of what packages are currently available for you.

---

### Post by Majestic 888 on 2009-07-27
I get
```

root@fatalms:~# apt-cache search sun java6 jdk
root@fatalms:~#
```

---

### Post by Majestic 888 on 2009-07-27
I got everything working guys. Thanks you all SOO much for all of your help:)

---

