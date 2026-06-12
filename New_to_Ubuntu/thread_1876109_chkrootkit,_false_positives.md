---
title: "chkrootkit, false positives?"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by fractalman on 2011-11-05
i just tried scanning with rkhunter and chkrootkit.  rkhunter comes back fine and my system appears to be clear but when i run chkrootkit i get the following 

The following suspicious files and directories were found:  

/usr/lib/jvm/.java-6-openjdk.jinfo

 /usr/lib/pymodules/python2.7/.path

I had a look at theses files but i don't know how they should look, they read as follows

> name=java-6-openjdk
alias=java-6-openjdk
priority=1061
section=main

hl java /usr/lib/jvm/java-6-openjdk/jre/bin/java
hl keytool /usr/lib/jvm/java-6-openjdk/jre/bin/keytool
hl pack200 /usr/lib/jvm/java-6-openjdk/jre/bin/pack200
hl rmid /usr/lib/jvm/java-6-openjdk/jre/bin/rmid
hl rmiregistry /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
hl unpack200 /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
hl orbd /usr/lib/jvm/java-6-openjdk/jre/bin/orbd
hl servertool /usr/lib/jvm/java-6-openjdk/jre/bin/servertool
hl tnameserv /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
hl jexec /usr/lib/jvm/java-6-openjdk/jre/lib/jexec
jre policytool /usr/lib/jvm/java-6-openjdk/jre/bin/policytool
jdk appletviewer /usr/lib/jvm/java-6-openjdk/bin/appletviewer
jdk apt /usr/lib/jvm/java-6-openjdk/bin/apt
jdk extcheck /usr/lib/jvm/java-6-openjdk/bin/extcheck
jdk idlj /usr/lib/jvm/java-6-openjdk/bin/idlj
jdk jar /usr/lib/jvm/java-6-openjdk/bin/jar
jdk jarsigner /usr/lib/jvm/java-6-openjdk/bin/jarsigner
jdk javac /usr/lib/jvm/java-6-openjdk/bin/javac
jdk javadoc /usr/lib/jvm/java-6-openjdk/bin/javadoc
jdk javah /usr/lib/jvm/java-6-openjdk/bin/javah
jdk javap /usr/lib/jvm/java-6-openjdk/bin/javap
jdk jconsole /usr/lib/jvm/java-6-openjdk/bin/jconsole
jdk jdb /usr/lib/jvm/java-6-openjdk/bin/jdb
jdk jhat /usr/lib/jvm/java-6-openjdk/bin/jhat
jdk jinfo /usr/lib/jvm/java-6-openjdk/bin/jinfo
jdk jmap /usr/lib/jvm/java-6-openjdk/bin/jmap
jdk jps /usr/lib/jvm/java-6-openjdk/bin/jps
jdk jrunscript /usr/lib/jvm/java-6-openjdk/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/java-6-openjdk/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-6-openjdk/bin/jstack
jdk jstat /usr/lib/jvm/java-6-openjdk/bin/jstat
jdk jstatd /usr/lib/jvm/java-6-openjdk/bin/jstatd
jdk native2ascii /usr/lib/jvm/java-6-openjdk/bin/native2ascii
jdk rmic /usr/lib/jvm/java-6-openjdk/bin/rmic
jdk schemagen /usr/lib/jvm/java-6-openjdk/bin/schemagen
jdk serialver /usr/lib/jvm/java-6-openjdk/bin/serialver
jdk wsgen /usr/lib/jvm/java-6-openjdk/bin/wsgen
jdk wsimport /usr/lib/jvm/java-6-openjdk/bin/wsimport
jdk xjc /usr/lib/jvm/java-6-openjdk/bin/xjc
plugin mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/

> 
/usr/lib/pymodules/python2.7
ubuntuone-control-panel
/usr/lib/pymodules/python2.7/ubuntuone-control-panel
ubuntuone-client
/usr/lib/pymodules/python2.7/ubuntuone-client
ubuntuone-storage-protocol
/usr/lib/pymodules/python2.7/ubuntuone-storage-protocol


i've never done any scans for rootkits before so i don't really know what to expect yet. Are these just false positives?

---

### Post by CharlesA on 2011-11-05
Both of those are notorious for false positives. It looks fine to me.

---

### Post by Dangertux on 2011-11-05
I would say false positives

---

