---
title: "Frostwire?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by fossil112 on 2008-11-10
Hi, I'm a beginner Ubuntu user and am trying to run frostwire on Ubuntu 8.10.  I've read [this archive thread]("http://ubuntuforums.org/showthread.php?t=662986&page=2") and am running into a somewhat similar issue.  
Here's what I see...

Run Frostwire:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
```

My java version:

```
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharin
```g)

Can you please assist?  Thank you!

---

### Post by fossil112 on 2008-11-11
Without knowing much about Ubuntu, does this mean the file has been incorrectly installed, or not installed yet?

```
Unable to access jarfile FrostWire.jar
```

---

### Post by nothingspecial on 2008-11-11
I may not understand your problem correctly but isn`t frostwire a torrent program?

Why not use deluge or transmission?

---

### Post by Dubbayoo on 2008-11-29
> **fossil112 said:**
> Hi, I'm a beginner Ubuntu user and am trying to run frostwire on Ubuntu 8.10.  I've read [this archive thread]("http://ubuntuforums.org/showthread.php?t=662986&page=2") and am running into a somewhat similar issue.  
Here's what I see...

Run Frostwire:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
```

My java version:

```
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharin
```g)

Can you please assist?  Thank you!

Run it as root first with 'sudo frostwire', configure it then run it again as your normal user account.

---

### Post by jamesstansell on 2008-11-30
> **fossil112 said:**
> Without knowing much about Ubuntu, does this mean the file has been incorrectly installed, or not installed yet?

```
Unable to access jarfile FrostWire.jar
```

Sounds like more of a configuration issue.

(Which, yes, _could_ be considered part of installation, but it's generally useful to be as specific as possible.)

---

### Post by loveandequality on 2008-12-10
i got the same thing well im just going to use limewire.

---

