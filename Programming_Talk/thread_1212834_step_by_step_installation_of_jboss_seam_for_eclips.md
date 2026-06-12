---
title: "step by step installation of jboss seam for eclipse"
date: 2009-07-14
forum: Programming Talk
---

### Post by burmanabhay88 on 2009-07-14
hey... I'm a newbie.
I have installed Eclipse Ganymede with some effort. What I need to do install JBOSS Server and Seam integrated into Eclipse...
can some1 help me out here. step by step preferabally
Am using Ubuntu 8.10.

---

### Post by johog on 2009-07-21
I have a nice jboss-seam development environment at Ubuntu 8.04.

I'm using java-6-sun-1.6.0.06. I guess you have already succeeded with your java installation.

The eclipse version I installed was a beta release of Jboss Developers Studio. 
It's using eclipse version 3.4.1 including 
JBossAS Tools			[http://jboss.org/tools](http://jboss.org/tools)
Seam Tools for Eclipse	[http://www.jboss.org/tools](http://www.jboss.org/tools)
Hibernate Tools for Eclipse	[http://tools.hibernate.org](http://tools.hibernate.org)

JBoss AS
First I installed Jboss-as in a separate jboss user ([http://ubuntuforums.org/showthread.php?t=652472](http://ubuntuforums.org/showthread.php?t=652472)) but that was not a good option for development (problem with hot deployment), this I probably a good production installation. Instead I created a directory in my home directory called Software.
Downloaded jboss-5.1.0.CR1-jdk6.zip ( [http://www.jboss.org/jbossas/downloads/](http://www.jboss.org/jbossas/downloads/) ) and extracted into the Software directory.
Create a symbolic link in the Software directory ( ln -s jboss-5.1.0.CR1 jboss-as )

JBoss Seam
Downloaded jboss-seam-2.1.2.CR2.tar.gz ( [http://www.seamframework.org/Download](http://www.seamframework.org/Download) )
and extracted into the Software directory.
Create a symbolic link in the Software directory ( ln -s jboss-seam-2.1.2.CR2 jboss-seam )

I'm using candidate releases you better go with the finale releases. (they were not available when I made my installations)
When you make references use the symbolic link names, that will make upgrades much easier.  

I don't like the project structure that the seam plug in for eclipse created, so I working exclusively with the seam-gen tool. You can create projects with the seam-gen tool that can be imported into eclipse. You have a nice tutorial here [http://docs.jboss.org/seam/latest/reference/en-US/html/gettingstarted.html](http://docs.jboss.org/seam/latest/reference/en-US/html/gettingstarted.html).

Don't forget to turn on the security in jboss-as before you go into production, by default it's off.

---

### Post by acho on 2009-12-20
i need to learn it too.... lets learn it.

---

