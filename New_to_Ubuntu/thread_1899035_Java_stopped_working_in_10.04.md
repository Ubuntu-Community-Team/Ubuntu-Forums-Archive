---
title: "Java stopped working in 10.04"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by Jetro on 2011-12-22
(I know this is a common one)

Java has become unusable in all my browsers. When I go to a web site that requires java, the page tells me I don't have it installed. I use the browsers [COLOR="RoyalBlue"]**Chromium**[/COLOR], [COLOR="Orange"]**Firefox**[/COLOR] & [COLOR="Red"]**Opera**[/COLOR].

The libnpjp2.so file (which I've seen suggested manyhwere) has at least been placed in Chromium's plugins folder, but no progress.

**Sun Java 6.0 Plugin** is installed, the same is **sun-java6-bin** and s**un-java6-jre**. These have been the solution to my previous java problems. Install them and it will work. I have however tried to re-install these to no avail. **Ubuntu restricted extras** is also installed.

Then I came across this tip:
```
sudo update-java-alternatives -l
```
To show the installed java versions and then set the "preferred" java version or something like that.
```
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
```
The jdk thing came on top, so I was suggested to set java-6-sun as the preferred one.

```
sudo update-java-alternatives -s java-6-sun
```
The results went like this:

```
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
```

The weird thing is that java was working just perfectly until suddenly. I haven't done anything nearly experimental in Lucid the last six months or so, except for updating updates.

---

### Post by ptn107 on 2011-12-22
You will need to install  openjdk-6-jre (or openjdk-7-jre if available) as the license for Sun java is no longer valid.  FYI this affects all versions of Ubuntu (and linux in general).

---

### Post by Jetro on 2011-12-22
It was already installed, but just to be sure, I reinstalled it. No difference, I'm afraid. 
openjdk-7-jre returned nothing after I searched for it.

---

### Post by QIII on 2011-12-22
As great as OpenJDK may be, it is only useful if the world recognizes it.  Often, it does not -- even though it is an open source implementation of the same thing.

I recommend installing the most recent version of Sun Java using the instructions here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Uninstall your current Sun Java first.

---

### Post by Miljet on 2011-12-22
There was an update a few days ago that broke the sun-java on all three of my machines. After much searching, I found that the link in /usr/lib/mozilla/plugins was missing. I used the following code to fix all of my systems.
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins
```
Bear in mind that all my systems are running 32 bit. Yours may be different if you are running 64 bit. If you get an error, try following the directories to make sure you have the same version and adjust as necessary.

Do not copy the libnpjp2.so file to the plugins directory. It has to be a soft link or it will crash. Almost all guides for installing sun-java suggest making the link in ~/.mozilla/plugins, but it seems to me that doing it that way would only make java available to the user that installed it. Putting it in /usr/lib/mozilla/plugins makes it available to all users.

---

### Post by 73ckn797 on 2011-12-22
> **QIII said:**
> [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

This is the solution. ^

---

### Post by Jetro on 2011-12-23
That fixed it, Miljet! Boy, that was easy (after you doing the hard work)!

Thank you ever so much, guys! :)

---

### Post by QIII on 2011-12-23
Actually, that didn't "fix it".  You now have an out dated and unsecure version ot Java that cannot be updated from the repos any longer.

---

### Post by Jetro on 2011-12-23
> **QIII said:**
> Actually, that didn't "fix it".  You now have an out dated and unsecure version ot Java that cannot be updated from the repos any longer.
So you have to uninstall what Java comes with Ubuntu, and follow that rather long guide to get a secure Java up and running, that will update itself? I don't even get the difference between Java, JRE, JDK and whatnot. 
IcedTea was always useless garbage in my case; never working.

---

### Post by 73ckn797 on 2011-12-24
My experience is that the openjdk package works well, generally. Some web sites where forms have to be filled out or photos uploaded can be problematic without the Sun package. Since I installed Sun-Java via the referenced link in the earlier comment, I was able to do my work without a hitch. The photo uploader I have to interact with worked perfectly. I have both installed, without the Icedtea Plugin.

---

