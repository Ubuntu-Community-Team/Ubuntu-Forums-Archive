---
title: "link group java is broken"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by meha on 2011-11-15
I am trying to install java on Ubuntu. Originally I installed Open JDK and then tried to install IBM Java based on some instructions on the web using tgz files I downloaded from IBM website (I need to be able to install websphere later). In this whole process I have completely messed up and now no java version is working. So I ran sudo apt-get install openjdk-6-jre and sudo apt-get install openjdk-6-jdk to at least let open jdk work. It ran successfully but when I run 
sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /opt/ibm/java/ibm-java-x86_64-60/jre/bin   1         manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode

Press enter to keep the current choice
[*], or type selection number: 2
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-6-openjdk/jre/bin/java because link group java is broken.
update-alternatives: warning: not replacing /usr/bin/java with a link.

I tried with option 0 also but the same result.

I have been getting this message since I tried to install IBM Java. What does " link group java is broken." really mean and what is its resolution.

---

### Post by meha on 2011-11-17
The issue got fixed. I had by mistake deleted the default java in /usr/bin and instead created a java folder in /usr/bin. I removed the folder and ran the same command again and the link was created.

---

