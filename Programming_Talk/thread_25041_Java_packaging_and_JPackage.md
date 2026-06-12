---
title: "Java packaging and JPackage"
date: 2005-04-09
forum: Programming Talk
---

### Post by goofrider on 2005-04-09
Historically Debian does not provide java packages (with a few exceptions), not even in non-free/contrib, all the while the JPackage RPM repository provides thousands of Java packages for RPM-based distros.

Is there any possibility of creating a Ubuntu APT repository for Java packages? Or working with JPackage to provide such repository? I'd be down for volunteering for such project.

It seems that Ubuntu's Java policy is even stricter than Debian, For instance, Tomcat4 is in Debian but soley absent in Ubuntu. Though I feel the free software philosphy is great and should be respected, it's important that there's a Java package repository for Debian/Ubuntu for those who need it, and when the day of a free Java VM comes, we wouldn't be caught with an empty Java repository. Wouldn't a third-party unofficial repo (like maybe hosting one on JPackage) be acceptable?

Can we somehow find a more pragmatic solution to the lack of Java packages in Ubuntu?

---

### Post by bored2k on 2005-04-09
The ubuntu backports have Sun's Java 1.5 .deb package specially made for Ubuntu (thank jdong for that). Or did I not understand what you wanted to say?

~$ apt-cache search jpackage
jpackage-utils - utilities for the JPackage Project

---

### Post by soul_rebel on 2005-04-09
Yes it would be nice. I think that most of jpackage rpms will work also in ubuntu if converted to debs and with jpackage-utils installed. Perhaps you should send a mail to one of the jpackage guys.

---

### Post by bored2k on 2005-04-09
[QUOTE=soul_rebel]Yes it would be nice. I think that most of jpackage rpms will work also in ubuntu if converted to debs and with jpackage-utils installed. Perhaps you should send a mail to one of the jpackage guys.[/QUOTE]
 What is it that you guys want exactly? JRE? JDK? Jdong did those for ubuntu already.

---

### Post by soul_rebel on 2005-04-09
if you don't understand what jpackage does just have a look at the website : [http://www.jpackage.org/](http://www.jpackage.org/)
bye

---

### Post by goofrider on 2005-04-09
[QUOTE=soul_rebel]Yes it would be nice. I think that most of jpackage rpms will work also in ubuntu if converted to debs and with jpackage-utils installed. Perhaps you should send a mail to one of the jpackage guys.[/QUOTE]


Have you actually used jpackage-utils? What does it actually do? How is it different from, say, using Alien to import the RPM?

My primary concern being that I'm not quite sure how rigid JPackage's packaging policy is and so using JPackage's RPM on a Debian/Ubuntu system might make a mess on the filesystem. Can you share your experiences?

---

### Post by soul_rebel on 2005-04-09
jpackage utils offer the infrastructure to run jpackage programs. It's a dependency. With than I think you can alien some rpms. Anyway I tryed to install eclipse from jpackage with alien and it didn't work.

---

### Post by goofrider on 2005-04-09
[QUOTE=bored2k]The ubuntu backports have Sun's Java 1.5 .deb package specially made for Ubuntu (thank jdong for that). Or did I not understand what you wanted to say?

~$ apt-cache search jpackage
jpackage-utils - utilities for the JPackage Project[/QUOTE]


I hate it when ppl treat me like a nooooooooooooooooooooooooob.  :-P 

JPackage began as a project to repackage Java binaries in RPM format, now it's become a complete RPM repository of thousands of open source Java binaries, complete with integration with package management tools in RPM-based distributions and dependency resolution.

What's the big deal you may ask. Well, if you ever have to install, say, some JSP/servlet webapps, you must first install Tomcat (presuambly unpack the tarball in /opt), then download the WAR file, and then maybe some Java library dependancies like Jakarta Commons Collections, ORO, or whatever.... Suddenly you're returned to dependancy hell, except in JAR format. Now rinse and repeat for all the other webapps you're installing in Tomcat, and don't even think about what you have to do if you want to test drive JBoss, Geronimo....

Not to mention that Java servers have conf files (which should've been in /etc), temp dirs (--> /tmp), data dirs (--> /var), etc. Installing these Java servers in /opt is un-Debian, makes backup difficult, and possibly insecure.

And at the end of the lesson I'd like to introduce you to the CLASSPATH env. The funnest part of a sysadmin job in configuring Java binaries. The problem is, CLASSPATH must be set to **each depended JAR file library**. Not just the path to some /jar-libs/*, but /jar-libs/jarfile1.jar; /jar-libs/jarfile2.jar...... Each and every one of them!!!!

While JPackage haven't solve all of these problems yet, but they're actively trying to address them. JPackage RPMs are tagged with dependcy metadata, and an RPM package management tool can download and install dependant packages from JPackage's repository automatically. Jpackage has borrowed Debian's alternatives system to handle multiple JVMs, and I'm not sure if they have suceeded in developing a system for automatic CLASSPATH resolution.

---

### Post by arashbi on 2008-02-08
I could not find anything that help me make jpackage work with ubuntu. Could somebody shed a lite on the situation with jpackage?
It is a really good tool when you are supposed to manage a bunch of java servers!

---

