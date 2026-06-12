---
title: "How to Set PermGen Max in Tomcat Startup.sh"
date: 2008-03-17
forum: Programming Talk
---

### Post by jebberwocky on 2008-03-17
Hello everyone

Currently I run into the problem of PermGen. In order to resolve it, I have to increase my PermGen. Does anyone know how could I do this in startup.sh?

---

### Post by dhoyt on 2011-07-27
Hi [jebberwocky]("http://ubuntuforums.org/member.php?u=519999").

There are many sources of information for tuning your tomcat install, but almost none of them have one crucial piece of information:  How to do this on an Ubuntu server.

The JVM options for tomcat6 are set in /etc/default/tomcat6:

```

# You may pass JVM startup parameters to Java here. If unset, the default
# options will be: -Djava.awt.headless=true -Xmx128m -XX:+UseConcMarkSweepGC
#
# Use "-XX:+UseConcMarkSweepGC" to enable the CMS garbage collector (improved
# response time). If you use that option and you run Tomcat on a machine with
# exactly one CPU chip that contains one or two cores, you should also add
# the "-XX:+CMSIncrementalMode" option.
JAVA_OPTS="-Djava.awt.headless=true -Xmx128m -XX:+UseConcMarkSweepGC -server"

```

You can change other startup options here as well.  Hope this helps!

---

