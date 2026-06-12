---
title: "Help needed in configuring multiple JVMs"
date: 2010-12-15
forum: Programming Talk
---

### Post by kc_student on 2010-12-15
Hi
My questions are about using Multiple JVMs (Java Virtual Machine) in Ubuntu.
I have installed Ububtu 10.10 in my system and it came preconfigured with openjdk 6. It contained both the JRE and JDK for OpenJDK 6.
I am trying to work on OpenJDK and HotSpot VM development in Ubuntu. Thats whyI downloaded and built another version of OpenJDk (OpenJDk 7) in my PC.
My build directory is /home/myname/devprojects/OpenJDK.
The default installation directory is /usr/lib/jvm/java-6-openjdk

My questiona are:
1. What are the environment variables that need to be set or configured so that my version of OpenJDK is used instead of the default installation? 
    Note: I have used export JAVA_HOME= /home/myusername/devprojects/OpenJDK/jdk7/j2sdk-image (this is where an image of my JDK is). But when I do printenv I don't find JAVA_HOME in the list of environment variables listed. Do I need to make an entry in the file .bashrc or etc/pofile (to change the PATH)or in both of them? Also can someone explain what are the uses of both these files?
2. In the folder /usr/lib/jvm of my PC, a new link to the folder /usr//usr/lib/jvm/java-6-openjdk. The name of the link is java-1.6.0-openjdk. Can anyone clarify the purpose of this link?
3. The /usr/bin contains a link to the Java executable to /etc/alternatives/java. I have tried to use the command sudo update-alternatives --config java. It gives the output "There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure." How do I use this command to configure the OpenJDk code (source code for Java) that I have downloaded and built from scratch?


myname@MyPC:~$ sudo update-alternatives --config java
[sudo] password for kanik: 
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.
myname@MyPC:~$ 

Any suggestion is welcome and appreciated.
Thanks and Regards,
KC

---

### Post by kwyto on 2010-12-15
[http://ubuntuforums.org/archive/index.php/t-9221.html]("http://ubuntuforums.org/archive/index.php/t-9221.html") 
This should answer most of your questions.

---

