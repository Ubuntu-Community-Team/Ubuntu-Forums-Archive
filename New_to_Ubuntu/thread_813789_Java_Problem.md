---
title: "Java Problem"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by OffHand on 2008-05-31
Hi Guys,

I am trying to get Java to work on my nightly builds Firefox which is installed in /opt/firefox/

Does anyone know where to create the symlink to?

---

### Post by ajmorris on 2008-05-31
which jre are you using, sun's or the open source one? When you have found which one you have installed, you can use apt to give a file contents list of the package, that will tell you where you can create the symlink to

AJ

---

### Post by OffHand on 2008-05-31
$ mlocate javaplugin
/etc/alternatives/xulrunner-1.9-javaplugin.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/openoffice/program/sunjavaplugin.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
/var/lib/dpkg/alternatives/xulrunner-1.9-javaplugin.so

$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

$ which java
/usr/bin/java

$ sudo update-alternatives --config javaPassword or swipe finger: 

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1a1pre) Gecko/2008052902 Minefield/3.1a1pre ID:2008052902 (location: /opt/firefox/)

---

### Post by OffHand on 2008-05-31
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

and 

sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so /opt/firefox/plugins/

and

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

Do not work...

---

### Post by ajmorris on 2008-05-31
> **OffHand said:**
> sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

and 

sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so /opt/firefox/plugins/

and

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

Do not work...

Strange... they should work, have you checked about:plugins in firefox, and also the plugin config path in about:config in firefox?

---

### Post by OffHand on 2008-06-01
> **ajmorris said:**
> Strange... they should work, have you checked about:plugins in firefox, and also the plugin config path in about:config in firefox?

about:config looks good. unfortunately I do not see Java in about:plugins

I'm kinda lost since everything seems to be installed and symlinked correctly. Maybe I should give V5 a try.

---

