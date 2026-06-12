---
title: "Firefox not picking up Java plugin"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by RapMasterC on 2008-06-24
For some reason Firefox will not run anything Java related anymore.  I'm still using the open-jre and icetea-plugin, however recently I installed (and removed suns java 6).  I now only have the open-jre and reqired packages installed.  I think FF is stuck trying to run a java-plugin that no longer exists (and I'm not sure how to change the symbolic links its using). 

I'm running Kubuntu 8.04 x64

heres some of the outputs that people seem to request:
```

shurtis@shurtis-desktop:~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

```
```

shurtis@shurtis-desktop:~$ ls -l /usr/lib/mozilla/plugins
total 1516
lrwxrwxrwx 1 root    root      37 2008-04-30 16:34 flashplugin-alternative.so ->
 /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root    root      45 2008-06-18 20:26 libjavaplugin.so -> /etc/alte
rnatives/xulrunner-1.9-javaplugin.so
-rw-r--r-- 1 root    root   31216 2008-03-31 22:34 mozplugger.so
-rw-r--r-- 1 root    root  290880 2008-05-13 07:31 mplayerplug-in-dvx.so
-rw-r--r-- 1 root    root    1067 2008-05-13 07:31 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root    root  290880 2008-05-13 07:31 mplayerplug-in-qt.so
-rw-r--r-- 1 root    root    1067 2008-05-13 07:31 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root    root  290880 2008-05-13 07:31 mplayerplug-in-rm.so
-rw-r--r-- 1 root    root    1067 2008-05-13 07:31 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root    root  290872 2008-05-13 07:31 mplayerplug-in.so
-rw-r--r-- 1 root    root  290880 2008-05-13 07:31 mplayerplug-in-wmp.so
-rw-r--r-- 1 root    root    1067 2008-05-13 07:31 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root    root    1067 2008-05-13 07:31 mplayerplug-in.xpt
lrwxrwxrwx 1 root    root      26 2008-06-18 20:40 nppdf.so -> /var/lib acroread                                                              /nppdf.so
lrwxrwxrwx 1 shurtis users     60 2008-04-30 16:29 npwrapper.libflashplayer.so - 
> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```
```

shurtis@shurtis-desktop:~$ find /usr/lib -iname '*javaplugin*'
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
/usr/lib/openoffice/program/sunjavaplugin.so
/usr/lib/firefox/plugins/libjavaplugin_oji.so

```
```

shurtis@shurtis-desktop:~$ readlink -f /usr/lib/firefox/plugins/libjavaplugin.so
/usr/lib/firefox/plugins/libjavaplugin.so

```

I've tried everything I can think of.

Thanks

edit:  I've also tried this
```

shurtis@shurtis-desktop:~$ sudo update-java-alternatives -s $(update-java-alternatives -l | cut -d' ' -f1)
No alternatives for appletviewer.
No alternatives for apt.
No alternatives for extcheck.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for idlj.
No alternatives for jar.
No alternatives for jarsigner.
No alternatives for javac.
No alternatives for javadoc.
No alternatives for javah.
No alternatives for javap.
No alternatives for jconsole.
No alternatives for jdb.
No alternatives for jhat.
No alternatives for jinfo.
No alternatives for jmap.
No alternatives for jps.
No alternatives for jrunscript.
No alternatives for jsadebugd.
No alternatives for jstack.
No alternatives for jstat.
No alternatives for jstatd.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for native2ascii.
No alternatives for rmic.
No alternatives for schemagen.
No alternatives for serialver.
No alternatives for wsgen.
No alternatives for wsimport.
No alternatives for xjc.
No alternatives for xulrunner-javaplugin.so.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/unpack200' to provide 'unpack200'.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-openjdk/bin/xjc
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer' to provide 'pluginappletviewer'.
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/policytool' to provide 'policytool'.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.

```

---

### Post by SIXAXIS on 2008-06-24
I know in Ubuntu, there is a package called "ubuntu-restricted-extras". I assume there is a Kubuntu version of that called "kubuntu-restricted-extras". That includes flash, Java, and other stuff.

---

### Post by RapMasterC on 2008-06-24
I have that package installed.  It was working previously, I just screwed something up and can't for the life of me figure out to get Java working in firefox again.  I believe they usually say the problem is occurring between the chair and the keyboard.

---

### Post by terrordrone on 2008-06-24
u might have tried this.. i might sound foolish

in FF3 a new plugin is disabled by default.. just goto addon->extensions and check if java is enabled..

---

### Post by avtolle on 2008-06-24
In the address bar of FF3, type "about:plugins" (w/o the quotation marks) and see what it reports as for a java plugin. If it shows the plugin for sun, try to remove it via Synaptic (if it shows that it is installed in Synaptic, that is). Otherwise, as you indicated, you will need to delete the sym link that was created earlier.

EDIT: OK, that is "about: plugins" (w/o the quotation marks and space).

---

### Post by philinux on 2008-06-24
Close FF.
Go into your FF directory and delete xpti.dat
Restart FF, it will rebuild this file. It's the register of plugins.

---

### Post by RapMasterC on 2008-06-24
It shows nothing for java under the about : plugins (without the spaces).  I've tried to delete xpti.dat and the pluginreg.dat

---

### Post by philinux on 2008-06-24
Backup your bookmarks and rename your .mozilla folder to let FF build a new one.

Before you do that have you tried.

sudo dpkg-reconfigure java

[edit] wrong command

should be
sudo update-alternatives --config java

---

### Post by RapMasterC on 2008-06-24
Tried letting FF build a new .mozilla, however, I still wont pick up any Java plugin

---

### Post by philinux on 2008-06-24
See my edit

---

### Post by avtolle on 2008-06-24
Is the plugin installed at all? I'm not familiar with Kubuntu, but check Synaptics to see if the plug in for the Open Java (f/k/a iced tea) is installed. If not, mark it for installation and apply.

---

### Post by RapMasterC on 2008-06-24
Tried both, the only the output of sudo update-alternatives --config java is
```

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.

```
and the plugin is installed.

---

