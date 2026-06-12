---
title: "Installing Oracle Java on Ubuntu 12.04 LTS"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by quantumax on 2013-10-27
[FONT=arial][SIZE=4][COLOR=#000000]Hi, dear All. I am new to Unix-like OS.
 
I was trying to install Oracle Java, using [/COLOR][[COLOR=#000000]http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux[/COLOR]]("http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux")[COLOR=#000000] .

I have completed successfully first 4 steps(from deleting Open Java to downloading  jre-7u45-linux-i586.tar.gz from java.com) and tried to proceed further:[/COLOR][COLOR=#545454]

[/COLOR]```
[B] cd /home/[B]"your_user_name"/Downloads

[/B][/B][B][B][B] sudo cp -r jre-7u40-linux-i586.tar.gz /usr/local/java

**[B][B][B] cd /usr/local/java**[/B][/B][/B][/B][/B][/B]

```[COLOR=#000000] 

The first and the second commands were executed without error message, but when I tried to execute the 3rd command I have recieved the message, that "java is a file, not a directory" or something like that. When I tried to create java directory [/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=arial]in /usr/local/[/FONT][/COLOR][FONT=arial][SIZE=4][COLOR=#000000], I recieved the message, that the directory "java" cannot be created if the file, named "java", already exists.


What am I doing wrong? Thanks[/COLOR][/SIZE][/FONT]

---

### Post by sammiev on 2013-10-27
You may want to look at [this]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html"), it will update on its own. Be sure to remove any installed java first. :)

---

