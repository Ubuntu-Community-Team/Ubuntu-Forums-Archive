---
title: "libXt.so.6: cannot open shared object file"
date: 2007-03-23
forum: Programming Talk
---

### Post by rehmke on 2007-03-23
I cannot seem to start a java web application (Apache Tomcat 5.5.20, Java 1.4.1) using Ubuntu Dapper server.  The webapp is simple, but does have the need to generate graphics, despite the server's *headless* configuration.

System:
- Linux ubuntu 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux

Exception:
[20070323-12:07:57][main] Unable to initialize application. /usr/local/j2sdk1.4.1_07/jre/lib/i386/libawt.so: libXt.so.6: cannot open shared object file: No such file or directory = java.lang.UnsatisfiedLinkError: /usr/local/j2sdk1.4.1_07/jre/lib/i386/libawt.so: libXt.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1473)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1389)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:832)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:507)
        at javax.swing.ImageIcon.<clinit>(ImageIcon.java:61)
        at com.infostructuresys.util.ResourceUtil.getImageIconFromJar(ResourceUtil.java:351)
        at com.infostructuresys.util.ResourceUtil.preCacheWebIcon(ResourceUtil.java:436)
        at com.infostructuresys.util.ResourceUtil.preCacheWebIcons(ResourceUtil.java:424)
	...

:confused: I have been able to resolve the same error on both current and older Fedora/RedHat deployments by installing deprecated x11 libraries or libxp6; no luck with Ubuntu yet...  Any thoughts?

Thanks,

R

~~~~~

---

### Post by Stemp on 2007-03-23
Hi rehmke,

Are you sure you don't need Java 5 for Tomcat 5 ?

---

### Post by rehmke on 2007-03-23
It should be noted that Apache Tomcat 5.5 has a compatibility layer to support Java 1.4.1 and 1.4.2 (this is very common for Apache's open source offerings for managing the foundation's libraries/utilities and the various versions of Java).  

The web application that I am using requires Java 1.4.1.  Thank you for the reply, but in this case, the version of Java is not directly related to the issue.  

The solution is likely related to installing requisite libraries, using apt-get to install dependencies such as libxp6 or x11-deprecated-libs; just not sure what packages to install in the context of Ubuntu.

---

### Post by Stemp on 2007-03-23
Assuming you are on i386 :
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libXt.so.6&searchmode=searchword&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libXt.so.6&searchmode=searchword&case=insensitive&version=dapper&arch=i386)
[http://packages.ubuntu.com/dapper/x11/libxp6.html](http://packages.ubuntu.com/dapper/x11/libxp6.html)

---

