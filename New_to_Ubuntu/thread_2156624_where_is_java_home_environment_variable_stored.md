---
title: "where is java_home environment variable stored"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by demecarv on 2013-06-22
I have installed java by these commands:

sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-java7-installer 
sudo update-java-alternatives -s java-7-oracle

If I understood properly these commands above garantee that java will update automatically.
I have been using Eclipse, STS and Tomcat successfully, then I believe that java is properly installed with its environments.
But I want to know where is the java_home environment.
I tried:
1)gedit /etc/environment
I found:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:$GRADLE_HOME/bin"
GRADLE_HOME="/opt/gradle/gradle-1.6"

2)whereis java (I believe that this is just a file find)
java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz

3)gedit ~/.pam_environment
But it is completly empty

4)gedit ~/.bashrc and after gedit .profile (I believe that this is just script files that run while starting linux).
But I didn't find any string with "java".

5)printenv JAVA_HOME (I believe that this only prints variables setted by export and it is valid only for the exact session you set) 
But nothing has printed.

Could someone help me find where is the java environment in my system and please adjust any wrong believes I wrote before?

---

### Post by 2F4U on 2013-06-23
This post explains how to set environment variable for Java:

[http://stackoverflow.com/questions/6477415/how-to-set-java-home-in-ubuntu](http://stackoverflow.com/questions/6477415/how-to-set-java-home-in-ubuntu)

And this is a documentation about environment variables in Ubuntu:

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

