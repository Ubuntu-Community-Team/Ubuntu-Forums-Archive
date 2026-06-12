---
title: "Eclipse Died Months After 3 Months"
date: 2008-02-11
forum: Programming Talk
---

### Post by ARam1024 on 2008-02-11
I installed Eclipse when I upgraded to Kubuntu 7.10.  I originally had some trouble, because I wasn't using Sun's version of Java, but I sorted that out.  Now after about three months, eclipse stopped working.  I get the following dialog box:

An error has occurred.  See the log file
/home/andrew/.eclipse/org.eclipse.platform_3.2.0/configuration/xxx.log

The log is:

!SESSION Mon Feb 11 16:55:20 EST 2008 ------------------------------------------
!ENTRY org.eclipse.core.launcher 4 0 2008-02-11 16:55:20.147
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ArrayIndexOutOfBoundsException: 0
	at org.eclipse.core.launcher.Main.getSplashLocation(Main.java:1642)
	at org.eclipse.core.launcher.Main.handleSplash(Main.java:1539)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

Eclipse was working properly yesterday.  I tried to install a few plugins via the update manager, but those failed, which I found strange (figured I work on that today - no such luck).  The only update I made today was installing ktorrent-kde4.  Here are the steps I've taken to try to resolve this:

- uninstall ktorrent-kde4
- remove/install eclipse
- reinstall eclipse (instead of remove then install)
- clearing workspace
- reinstall java (sun)
- install sun's SDK

I get the same error message each time.

Installed Java:

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/j2se/1.4/bin/java

java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

Any help would be much appreciated.

[NOTE: the original topic for this post was going to be Eclipse Died After 3 Months - sorry about the odd phrasing]

---

### Post by lnostdal on 2008-02-11
maybe clearing the configuration files(#1) in your home directory would help .. removing or reinstalling the software does not remove or reset these configuration files

#1: not everything ofc .. just the stuff related to eclipse

---

### Post by ARam1024 on 2008-02-15
Thanks for the help.  I actually had to reinstall Kubuntu though.  Piecies of the OS simply broke, and the eclipse problems I was having were just symptomatic of the larger problem.

---

