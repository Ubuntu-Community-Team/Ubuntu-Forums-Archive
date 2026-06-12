---
title: "java executable jar freezes"
date: 2008-06-25
forum: Programming Talk
---

### Post by mdawg414 on 2008-06-25
I am exporting an executable jar with Eclipse that has a javax.swing GUI and it used to work fine but now when I run the jar file like so:
# java -jar myfile.jar
the GUI pops up but I cannot interact with it at all. Basically, the buttons are there and everything but I cannot click on anything. I tried putting the jar on another machine running CentOS and it works fine.

Any ideas what it could be? All of my other jars have the same problem on this machine (running ubuntu 8.04)

Thanks!

---

### Post by cpetercarter on 2008-06-25
It may be that more than one flavour of Java is installed on the machine and that /usr/bin/java is pointing at the wrong one. See [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") and try running 
```
sudo update-alternatives --config java
```

I am by no means an expert in this area, but by coincidence I ran this command earlier today, as much to see what would happen as anything else, and changed the "default" Java, and was amazed to find that a jar file which I had abandoned as broken now worked.

---

### Post by mdawg414 on 2008-06-25
Thanks for the response. No luck though. When I ran that command I had "two alternatives which provide 'java'"
/usr/bin/gij-4.2
/usr/lib/jvm/java-gcj/jre/bin/java

The second one was the default one and when I tried changing the default to the 1st one the same thing happened.

I should also add that I am using java 1.5. Any other ideas? Do I maybe have to update my java installation? I just installed it a few weeks ago

---

### Post by mdawg414 on 2008-06-25
Ok I figured something out. The path the 'alternative' was pointing to earlier is not the path of the java executable I want it to use. It points to /usr/lib/jvm/java-gcj/jre/bin/java but it should point to /home/matt/SDK/jdk/bin/java

I could just go into /usr/bin and change the symbolic links of java, javac, etc to the correct folder, but right now they are pointing to /etc/alternatives/java and that sounds somewhat important. Is there any risk changing that? What could have cause this re-route to happen?

---

### Post by cpetercarter on 2008-06-25
I have sunjava-6. What flavour of Java do youhave on the machine on which your jar files run?

---

### Post by mdawg414 on 2008-06-25
Well I thought it was 1.5 since when I ran java -version I got back 1.5 but if I run that command with the correct java file here is the output:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode)

---

### Post by mdawg414 on 2008-06-25
I decided to man up and use the alternatives function built into ubuntu. I just added my new jdk as a new alternative for all of the relevant java commands (java, javac, javadoc) and had it point to the correct executable. 

Here is the command I wrote for installing a new alternative for the java executable:
# sudo update-alternatives --install /usr/bin/java java /home/matt/SDK/jdk/bin/java 3

Thanks for your help though peter!

---

### Post by jamesstansell on 2008-06-25
> **mdawg414 said:**
> I decided to man up and use the alternatives function built into ubuntu. I just added my new jdk as a new alternative for all of the relevant java commands (java, javac, javadoc) and had it point to the correct executable. 

Here is the command I wrote for installing a new alternative for the java executable:
# sudo update-alternatives --install /usr/bin/java java /home/matt/SDK/jdk/bin/java 3

Thanks for your help though peter!

Hi Matt,

I never knew you could do that.  Nice to find out.

How did you install /home/matt/SDK/jdk/bin/java ?

---

### Post by geirha on 2008-06-26
There are java 6 in the repositories. Any reason why you need to have it in your home-directory? 

[sun-java6-jre](apt:sun-java6-jre) 
[sun-java6-jdk](apt:sun-java6-jdk)

---

