---
title: "Kubuntu:  Eclipse Javadoc popups don't include links"
date: 2011-10-18
forum: Programming Talk
---

### Post by kvdbreem on 2011-10-18
Hey all.  I'm trying to use Eclipse in KDE and it's working great.  Only problem is that the links (ie words in javadoc comments annotated with @link annotation) aren't underlined and aren't clickable.  So when I hover the mouse over a class or method for example and the javadoc for it includes a link to another class that link isn't clickable, so I can't browse around in the popup.

Any ideas what the problem here might be?

Ubuntu version=Kubuntu 11.10
KDE version info
Qt: 4.7.4
KDE Development Platform: 4.7.1 (4.7.1)
KDE Daemon: $Id$

Eclipse Version
Version: Helios Service Release 1
Build id: 20100917-0705
Installed JRE version 1.6

---

### Post by kvdbreem on 2011-10-25
I just installed the latest Eclipse (Indigo) and now I can see the links.  Still not sure what the issue was.

---

### Post by Danimoth on 2012-05-06
Have the same issue with freshly installed 12.04 with eclipse indigo, openjdk-7. Don't know where to look for a solution.

---

### Post by r-senior on 2012-05-06
If you go to Window-Preferences, then find Java > Installed JREs, select your JDK and Edit. In the list of JAR files, select them all and hit the JavaDoc location button. 

Set the JavaDoc location path to [http://download.oracle.com/javase/7/docs/api/](http://download.oracle.com/javase/7/docs/api/)

Obviously that's a web URL. You can also install the openjdk-7-doc package locally and specify the location of the docs, which will be something like file:/usr/share/doc/openjdk-7-jdk/api/. Make sure you press the validate button to check it's OK.

If you have the JavaDoc locally installed, you can also open it in your web browser with file:///usr/share/doc/openjdk-7-jdk/api and bookmark it.

---

