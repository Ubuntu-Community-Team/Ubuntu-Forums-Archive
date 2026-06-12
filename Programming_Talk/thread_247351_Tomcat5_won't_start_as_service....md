---
title: "Tomcat5 won't start as service..."
date: 2006-08-30
forum: Programming Talk
---

### Post by skaboss on 2006-08-30
Hello,

I have a strange (and disturbing) problem :
installed tomcat5 via apt. It won't start automatically at system start up, instead, i have to launch it via ```
sudo /etc/init.d tomcat5 start
```

What did i miss ?

Thanks for your help.

---

### Post by octopocky on 2006-08-30
This is my first Ubuntu server so it's a bit of an experiment for me too. I'm running Xubuntu 6.06.

I did the following:

$ sudo nano /etc/environment

and added the following line:

JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun-1.5.0.06"

This got tomcat5 to run from the command line with no other problems. In my case, it won't start at boot-up.

---

### Post by octopocky on 2006-08-30
I've done the following:

sudo rm /var/log/tomcat5/*

That removed the log files. I rebooted the machine and checked the log files. There are none. Is there some file I can add a command line to get Tomcat5 to start up?

---

### Post by JimTDI on 2006-11-09
> **octopocky said:**
> I've done the following:

sudo rm /var/log/tomcat5/*

That removed the log files. I rebooted the machine and checked the log files. There are none. Is there some file I can add a command line to get Tomcat5 to start up?

> **skaboss said:**
> Hello,

I have a strange (and disturbing) problem :
installed tomcat5 via apt. It won't start automatically at system start up, instead, i have to launch it via ```
sudo /etc/init.d tomcat5 start
```

What did i miss ?

Thanks for your help.


I had the same problem at first, and did a few simple things and got it to start.

Download and install Sun Java from the Ubuntu repositories.

edit the file /etc/default/tomcat5 and pay attention to the JDK and Tomcat User lines.  Here's what I have:

[COLOR="Blue"][SIZE="1"]# Run Tomcat 5 as this user ID (default: tomcat5). Set this to an empty string
# to prevent Tomcat from starting.
TOMCAT5_USER=tomcat5

# The home directory of the Java development kit (JDK). You need at least
# JDK version 1.3, just the Java runtime environment (JRE) will not work
# because a Java compiler is needed to translate JavaServer Pages (JSP).
# If JAVA_HOME is not set, some common directories for the non-free JDKs
# as packaged by the Debian java-package and the directories of
# java-gcj-compat-dev and kaffe are tried.
#
# You can also set JSSE_HOME here to enable SSL support
# (this is automatically done for JDK 1.4+, java-gcj-compat-dev and kaffe).
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06
#JAVA_HOME=/usr/lib/jvm/java-gcj
#JSSE_HOME=/usr/local/jsse

# Directory for per-instance configuration files and webapps. It contain the
# directories conf, logs, webapps, work and temp. See RUNNING.txt for details.
# Default: /var/lib/tomcat5
CATALINA_BASE=/var/lib/tomcat5

# Arguments to pass to the Java virtual machine (JVM)
# "-Djava.awt.headless=true -Xmx128M" is automatically set if CATALINA_OPTS
# is left empty here
#CATALINA_OPTS="-Djava.awt.headless=true -Xmx128M -server"

# Java compiler to use for translating JavaServer Pages (JSPs). You can use all
# compilers that are accepted by Ant's build.compiler property.
#JSP_COMPILER=jikes

# Use the Java security manager? (yes/no, default: yes)
#TOMCAT5_SECURITY=yes

# Timeout in seconds for the shutdown procedure (default: 30). The Java
# processes will be killed if tomcat5 has not stopped until then.
#TOMCAT5_SHUTDOWN=30

# Number of days to keep old log files in /var/log/tomcat5 (default: 14)
LOGFILE_DAYS=30[/SIZE][/COLOR]

Reboot - and most important - it was not on the port I've seen others say it is.  Mine is at:  [http://localhost:8180](http://localhost:8180)

Running Dapper 6.06LTS here...

Good luck - let me know if this works for you! :)

---

