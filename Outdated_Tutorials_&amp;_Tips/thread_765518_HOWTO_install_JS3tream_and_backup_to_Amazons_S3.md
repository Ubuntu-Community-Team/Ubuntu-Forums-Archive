---
title: "HOWTO: install JS3tream and backup to Amazons S3"
date: 2008-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Skidd on 2008-04-24
JS3tream is a simple utility that bridges between TAR and Amazons S3 service.   [http://js3tream.sourceforge.net/](http://js3tream.sourceforge.net/)

You'll need Java 1.5+ and JS3tream.

Install the Sun JVM
```

castle ~# apt-get install sun-java5-bin

```

You will need the zip/unzip utility to extract the JS3tream utility
```

castle ~# apt-get install unzip

```

Go to the JS3tream web site, and download the latest zip file.  Extract this file to a directory of your choice.  Eg /usr/local/bin
```

castle ~# cd /usr/local/bin
castle ~# unzip js3tream-0.6.2.zip

```

Test to make sure both java and JS3tream are correctly setup.  Start by going to the directory you put JS3tream.
```

castle ~# cd /usr/local/bin

```

Make sure java is correctly installed.  I happen to have 1.5.0.11
```

castle ~# java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode)

```

Test that JS3tream can be executed.
```
castle ~# java -jar js3tream.jar --help
JS3tream v0.6 - December 17, 2007
Protected under the LGPL
Copyright (c) Shane Powell 2007
http://js3tream.sourceforge.net

```

At this point JS3tream should be correctly installed.  Now, it's simply a matter of following the examples and howtos on the JS3tream web site.

I've been using JS3tream to backup my entire mp3, home movie and photograph collection for a little over a year now.  Thankfully, I've only needed to restore some of my photos once.

Enjoy!
Shane.

---

