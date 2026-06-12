---
title: "Install tomcat6.0.18 JAVA_HOME/JRE_HOME problem"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Grace.zhang on 2008-11-10
Firstly, I install java-6-sun
then I download tomcat6.0.18
then I set JAVA_HOME with every method(in ./.bashrc, /etc/profile, etc) I can find online. 
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/
Also, I have the result:

tai@avaceratops:~$ echo $JRE_HOME
/usr/lib/jvm/java-6-sun/jre

however, when I try to start tomcat, I got:
tai@ubuntu:/$ sudo /usr/local/tomcat/bin/startup.sh
Using CATALINA_BASE: /usr/local/tomcat
Using CATALINA_HOME: /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME: /usr

it's weird, it should be Using JRE_HOME: /usr/lib/jvm/java-6-sun/jre in my last line based on the value of my JRE_HOME
can anyone give me any hint? thank you!

---

### Post by quirks on 2008-11-10
Sudo resets the environment variables. When you run sudo, JRE_HOME is reset to its default (probably null) and Tomcat will assume its own default (/usr). You can run sudo with the -E switch to preserve the environment.

Are you sure, you must run the script as root? I have no idea how to set up Tomcat, but it is usually a good practice to run servers as a dedicated user instead of as root.

---

