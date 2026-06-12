---
title: "trouble configuring javaee 5"
date: 2009-11-24
forum: Programming Talk
---

### Post by vra5107 on 2009-11-24
Hello

         I have been trying to install javaee 5. I downloaded the zip file and installed it in /opt. When *which java* is run, the following is the output.

[I]
vensoft@ven-10-c11:/opt/SDK$ which java
/usr/bin/java
vensoft@ven-10-c11:/opt/SDK$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2009-11-05 12:55 /usr/bin/java -> /etc/alternatives/java
vensoft@ven-10-c11:/opt/SDK$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2009-11-05 12:55 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java
[/I]

after reading a few blog posts I concluded I have to change the environment variables in the /etc/bash.bashrc file. The following are the changes I made.

[I]export JAVA_HOME="/opt/SDK/jdk"
export CLASSPATH="/opt/SDK/jdk/lib"
[/I]

When I check for the values of these variables everything seems fine.

[I]
vensoft@ven-10-c11:/opt/SDK$ echo $JAVA_HOME
/opt/SDK/jdk
vensoft@ven-10-c11:/opt/SDK$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
[/I]

but when run *which java* again the result is the same.

So I tried adding these variables s to the */etc/environment * file. This one show weirdness of its own. When I save the file everything is saved, but when I try to *echo* the variables they are all blank.

I am relatively new to linux usage. Could some one help me .

Thanks
Venkat

---

### Post by baizon on 2009-11-24
Try that: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by vra5107 on 2009-11-24
Thanks for the reply. Thats another thing I forgot to mention. when
sudo update-java-alternatives -l I see only one alternative.

[I]
vensoft@ven-10-c11:/opt/SDK$ sudo update-java-alternatives -l
[sudo] password for vensoft: 
java-6-sun 63 /usr/lib/jvm/java-6-sun
[/I]

Is there a way I can add another alternative. I tried the --install command but with no result.

sudo update-alternatives --verbose --install /usr/bin/java java /opt/SDK/jdk/jre/bin/java 1

vensoft@ven-10-c11:/opt/SDK$ update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun


I still see only one option.

Thanks

---

### Post by baizon on 2009-11-24
Have you tried that: [http://ubuntuforums.org/showthread.php?t=366104]("http://ubuntuforums.org/showthread.php?t=366104") ?

---

