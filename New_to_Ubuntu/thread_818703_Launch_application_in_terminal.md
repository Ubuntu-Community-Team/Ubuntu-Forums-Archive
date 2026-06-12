---
title: "Launch application in terminal"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by JeppeM on 2008-06-04
Hey guys,

I've having a weird problem - I've written a basic bash script that will start a few programs for when i develop stuff. The script can be viewed in the last part of the post.

Now, when i try to launch it from the terminal window by doing /development/start (as my normal user - no sudo etc), it works fine, and it starts the script like it should.

However, when i try to create a launcher for my panel, and create a launcher with "application in terminal" with the command /development/start, it doesn't act like it should. It prints something about dirname: missing operand, and doesn't see my JAVA_HOME variable, even though, when I'm in the normal terminal, it does recognize JAVA_HOME.

Is there anyone here who can explain this for me? :P

Here's the script:
```
echo '* Starting JBoss'
/usr/local/jboss/bin/run.sh > /development/logs/jboss_runtime.log &
echo '* Waiting 20 secs to make sure that polopoly has started'
sleep 20
echo '* Starting Polopoly'
/development/polopoly/bin/polopoly start > /development/logs/polopoly_start.log
echo '* Starting Apache Tomcat'
/usr/local/tomcat/bin/startup.sh
echo '* Truncating Apache Tomcat log'
cat /dev/null > /usr/local/tomcat/logs/catalina.out
echo '* Moving to Apache Tomcat'
tail -f /development/logs/tomcat.log
```
Which gives this (correct) output when run from the terminal:
```
jeppe@jeppe-laptop:~$ /development/start
* Starting JBoss
* Waiting 20 secs to make sure that polopoly has started
* Starting Polopoly
* Starting Apache Tomcat
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun
* Truncating Apache Tomcat log
* Moving to Apache Tomcat
```
But it gives this (not expected) output when i run the same script from the panel launcher:
```
* Starting JBoss
* Waiting 20 secs to make sure that polopoly has started
* Starting Polopoly
dirname: missing operand
Try `dirname --help' for more information.
dirname: missing operand
Try `dirname --help' for more information.
* Starting Apache Tomcat
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
* Truncating Apache Tomcat log
* Moving to Apache Tomcat
```
And Tomcat doesn't start up like it should - Cause there's no JAVA_HOME when i use the launcher, but it's there when i use the terminal, even though the launcher is of the type "Application in terminal".

---

### Post by sayakb on 2008-06-04
Try:
```
gnome-terminal -e /pathtoscript
```

---

### Post by JeppeM on 2008-06-04
No luck - still does it the same way with the wrong output, i just tried both as Application and Application in terminal

---

