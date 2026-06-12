---
title: "packages for NetBeans"
date: 2010-05-03
forum: Programming Talk
---

### Post by satimis on 2010-05-03
Hi folks,


Ubuntu 10.04 Lucid


I'm prepared using NetBeans to learn Java.  Please advise which package I need to install?

On Ubuntu repo

$ apt-cache search netbeans | grep java```

gcj-4.4-source - GCJ java sources for use in IDEs like eclipse and netbeans
libbeansbinding-java - Beans Binding API
libbeansbinding-java-doc - Beans Binding API
libnb-apisupport1-java - Common NetBeans Platform Development Related Libraries for NetBeans
libnb-ide12-java - Common Integrated Development Environment Libraries for NetBeans
libnb-java3-java - Common Java Related Libraries for NetBeans
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-platform-devel-java - Build harness for NetBeans Platform
libnb-platform11-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform11-java-doc - NetBeans Platform javadoc
libnetbeans-cvsclient-java - NetBeans CVS Client library
libopenide-util-java - OpenIde utility library
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation

```


$ apt-cache search netbeans | grep ide```

libnb-ide12-java - Common Integrated Development Environment Libraries for NetBeans
libopenide-util-java - OpenIde utility library

```

Which of them will I need?  Please help.  TIA


B.R.
satimis

---

### Post by Zugzwang on 2010-05-03
Note that "grep" is case-sensitive by default. So you missed the main package simply called "netbeans":

```

$ apt-cache search netbeans | grep -i Java
libbeansbinding-java - Beans Binding API
libbeansbinding-java-doc - Beans Binding API
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-platform-devel-java - Build harness for NetBeans Platform
libnb-platform9-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform9-java-doc - NetBeans Platform javadoc
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation
libnb-apisupport1-java - Common NetBeans Platform Development Related Libraries for NetBeans
libnb-ide10-java - Common Integrated Development Environment Libraries for NetBeans
libnb-java2-java - Common Java Related Libraries for NetBeans
netbeans - Extensible Java IDE

```

So simply install the "netbeans" package.

---

### Post by satimis on 2010-05-04
> **Zugzwang said:**
> -snip -
So simply install the "netbeans" package.

Hi,

Thanks for your advice.

I got Netbeans installed.  It is now running.

Coming to the manual/tutorial for a beginner learning Java, google found me many of them including YouTube video. Where shall I start? How to select the right one? Could you please shed me some light? TIA

B.R.
satimis

---

