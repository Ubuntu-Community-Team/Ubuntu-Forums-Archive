---
title: "GWT fails to launch sample apps"
date: 2007-08-30
forum: Programming Talk
---

### Post by kickabear on 2007-08-30
I've downloaded GWT (Google Web Toolkit) from Google, and untarred it.  I tried to lauch the KitchenSink sample app, but get an error similar to the one below.  I tried to create a new app, and I got the following error:

[INDENT]Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.IllegalArgumentException: URI "file:./gwt-dev-linux.jar" is not hierarchical
   at java.io.File.<init>(libgcj.so.70)
   at com.google.gwt.util.tools.Utility.computeInstallationPath(Utility.java:287)
   at com.google.gwt.util.tools.Utility.getInstallPath(Utility.java:223)
   at com.google.gwt.util.tools.ToolBase.<clinit>(ToolBase.java:55)
   at java.lang.Class.initializeClass(libgcj.so.70)[/INDENT]

I've tried searching, but I can't find anything related to this one.  Any help would be great.  Thanks!

---

### Post by hopp on 2007-09-03
On 7.04 I found that it was because GCJ was installed.

```
sudo apt-get remove gcj libgcj-common libgcj7-0
```

and installing a sun jdk cleared it right up.

---

### Post by bozinsky on 2008-01-04
This works, but actually removing gcj removes eclipse by the way.

Viktor provides solution there: 
[QUOTE=viktor.ilijasic;3306826]

```

sudo update-java-alternatives -s java-6-sun
```

This works with eclipse 3.2.2 & sun-java6-jdk

---

### Post by kballero on 2008-10-31
You may also need the GNU C++ Library (I did!)

aptitude install libstdc++5

:popcorn:

---

### Post by davejoyce13 on 2008-12-11
I'm running Intrepid, with OpenJDK 6 and Eclipse 3.4.1 (Ganymede) installed. I downloaded the GWT distribution for Linux and followed the instructions in the section [Creating an Application from Scratch (with Eclipse)]("http://code.google.com/webtoolkit/gettingstarted.html#NewEclipse").

When I clicked the 'Run' button, I was getting an ```
UnsatisfiedLinkError: cannot resolve libstdc++.so.5
```

Based on the above suggestion, I just ran [FONT="Courier New"]**apt-get install libstdc++5**[/FONT] and that completely fixed the problem.

Thanks!

---

### Post by hellz99 on 2009-01-02
Yep, went through the same thing.  Here's a [guide on configuring GWT and ubuntu]("http://whatwouldnickdo.com/wordpress/99/unable-to-load-mozilla-for-hosted-mode-gwt-ubuntu-810-linux/").

---

