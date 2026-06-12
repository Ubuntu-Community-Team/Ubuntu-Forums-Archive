---
title: "Tomcat 5.5 problem"
date: 2005-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by scelter on 2005-11-30
I'm having trouble starting apache tomcat 5.5 on my ubuntu machine.
When i do:
*/usr/local/tomcat/bin/startup.sh*
I get following error: 
[I]Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program[/I]

When i echo $JAVA_HOME, I get:
*/usr/local/jdk1.5*

This is the directory where i installed java.
[I]# ls /usr/local/jdk1.5/
bin  COPYRIGHT  demo  include  jre  lib  LICENSE  man  README.html  sample  src.zip  THIRDPARTYLICENSEREADME.txt[/I]

java -version gives me:
[I]java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)
[/I]

What I find weird is that this configuration worked fine a few days ago. When I tried to startup tomcat yesterday, It failed. I've tried to reinstall tomcat and java, but this doesn't solve the problem. Any suggestions on how to solve this problem?

---

### Post by emperon on 2006-01-07
How did you install your java ? It is not the default directory you are using if you follow up the guidlines in this forum to install JDK. Also take a look at this post.
Same problem with yours:
[http://www.ubuntuforums.org/showthread.php?t=23340&highlight=tomcat](http://www.ubuntuforums.org/showthread.php?t=23340&highlight=tomcat)

---

