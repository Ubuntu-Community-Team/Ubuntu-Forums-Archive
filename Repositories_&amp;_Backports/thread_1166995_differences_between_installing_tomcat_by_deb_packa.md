---
title: "differences between installing tomcat by deb package or tgz"
date: 2009-05-22
forum: Repositories &amp; Backports
---

### Post by michaelrepucci on 2009-05-22
I'm posting this partly to garner insightful responses that would help me understand the original package developers intentions, and partly just to help people who might struggle with some of the same issues as myself.

I have found over the past week that installing Tomcat (either version 5.5 or 6) from the packages (via Synaptic Package Manager, or apt-get) is significantly more error prone and difficult, in the long run, than installing from the tar-zipped download. Now, I'm using Tomcat simply for development purposes, and I presume that there are many advantages to installing Tomcat by package for actual server usage, though, if that's true, it isn't explained anywhere that I can find.

The big differences, for my purposes, are two-fold. Firstly, Tomcat 5.5 when installed by package runs on port 8180, not 8080. (You can discover this through a Google search, but it's not a fun thing to debug when you're a newbie to Tomcat, as I am.)

Secondly, and more importantly, there is a startup script installed by the package (/etc/init.d/tomcat* and linked in /etc/rc*.d/), which differs from the startup script $CATALINA_HOME/bin/catalina.sh. I would love to know why the package developers thought the included startup script wasn't good enough, especially because, for my purposes, it is actually superior.

Using the /etc/init.d/tomcat* script spawns three processes (see [http://ubuntuforums.org/showthread.php?t=1165023](http://ubuntuforums.org/showthread.php?t=1165023)), and Tomcat runs fine, including the manager and example apps. However, a custom app provided by my colleague fails. This app runs fine on multiple other systems, and DOES run fine on my system as well if I use $CATALINA_HOME/bin/catalina.sh to start Tomcat instead (which, incidentally, spawns only one process). So what is the difference between these startup scripts? And why do the package maintainers (presumably) believe their scripts to be a preferred way to run Tomcat (i.e., what am I losing by using $CATALINA_HOME/bin/catalina.sh)?

I'm not so concerned about making my custom app work with the /etc/init.d/tomcat* script startup method, since this is just for development purposes. I'm more curious to understand the difference between the various scripts as they relate to Ubuntu packages and Tomcat operation and functionality. But just in case you were curious, the error I get with my custom app when running using the /etc/init.d/tomcat6 script says something about a parsing error in {my app}/WEB-INF/web.xml, which doesn't occur when Tomcat is started with $CATALINA_HOME/bin/catalina.sh.

Thanks in advance for any insight! And I hope this helps others with the same problem.

:) Michael

---

