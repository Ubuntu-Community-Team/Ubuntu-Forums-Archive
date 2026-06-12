---
title: "How to install J2EE"
date: 2007-02-15
forum: Programming Talk
---

### Post by syalam on 2007-02-15
Is there a way to install J2EE from synaptic? All Sun has is a bin file. Any help would be appreciated as I am new to Linux. Thanks!

---

### Post by hod139 on 2007-02-15
Do you want J2EE ( Java Platform, Enterprise Edition) or the Java development kit.  If the former, it is not in synaptic you will have to download it from Sun.  If the latter, it is in the repo under sun-java.

---

### Post by syalam on 2007-02-15
I wanna write J2EE code...so I'm guessing i need to get it from SUN ya?

---

### Post by lloyd mcclendon on 2007-02-16
just stick with php.  if you can't figure out how to get the sdk installed it's pretty much hopeless  [www.sun.com](www.sun.com)  click download, jee6 linux .bin.  google for how to extract a tar file, or better yet just search this forum, this comes up all the time.

then get eclipse and an app server, tomcat with open ejb is the easiest, jboss is cool if you've got the patience and hardware.

---

### Post by syalam on 2007-02-16
haha id do it in php except ive gotta do my HW assignment in Java

---

### Post by Ramses de Norre on 2007-02-16
Download the .bin file for linux from sun's website, run **chmod +x *.bin && ./*.bin**, replace '*' by the actual file name.
You know have a directory with the executables and such.

---

### Post by sunshineboy on 2008-08-03
when i install j2ee.bin,something weird just happen .
the installing process is stumbled.........show "deleting  temp file " and then no response.
someone who know why..
thks...

---

### Post by tinny on 2008-08-03
If you are a beginner wanting to play with J2EE, get [NetBeans]("http://download.netbeans.org/netbeans/6.1/final/") installed. It has everything bundled ready to go.

BTW: J2EE is a little different from J2SE in the fact that you dont really have a proper JDK for it. Usually you will just be using the J2SE JDK + the runtime library's of the servlet container you plan to deploy too (E.g. The jars within Tomcat that provide the J2EE type functionality).

It is best for you to first start J2EE development with a working setup (NetBeans) and then over time you can slowly learn how its all put together.

---

### Post by razorxpress on 2008-10-18
J2ee consists of n-tier( different layers) application development. At minimum you have a part getting data from database (using object relational mapping technology. i.e use database components like object in java and work that way). Next layer is the business layer. In business layer you write how the calculation from the database is done on behalf of the client. The last layer is the client layer. You have many options here. You can decide for yourself how the client will interect with the business working on data. E.g Swing interface, web interface, applet etc. In this layer you will write how the client will be able to work with the programming business. Now at client and business you can add more layers as of requirement. Don't confuse layers with anything else. It's minimum of java classes which does behave some predefined way, and are written by following some standard, which say they are at some layer. So while developing any J2EE application you need to have is JDK installed(from sun site. It's same jdk which you need to write normal java applications). An application server(not apache tomcat if you need EJB),  database server (as you want like mysql, postgresql, mssql etc) and many many jar files to follow different specification at different layers. So there is no point on saying what i will install to develop j2ee. Linux can do is let you install ant, maven2, jdk. Now you need jar files as some tutorials suggest you while you are reading some of them. Starting ejb at first is what i don't suggest. EJB development include many things so i suggest you first read things like JSF, annotation, persistence, POJO, java messaging service (JMS). They are individual components that help you learn EJB. For lightweight you can start learning springframework. It is an alternative to EJB and very sucessfull. If you need to interact thousand of user at one time (I mean big apps you will probably develop apps on ejb). For lightweight springframwork is good. With it's built in logging, hibernate (persistence), unit testing features. So don't start searching how to install j2ee. The answer is install ide like eclipse or netbeans and you have all the required packages installed except some required databases (but with netbeans you have glassfish, which you have to choose while installing). Eclipse is nice though to write apps (With netbeans you fill like you are writing something over a swing (little slow). Use eclipse with option eclipse -vmargs -XX:MaxPermSize=256m so that you have enough memory for eclipse. IDE's like eclipse and netbeans not only provide jar files you need with the ejb development but also provide directory structure for source files, class files, integrate with database, make easy to include other jar files, help while writing codes(so you make less mistake), and make a perfect environment for ejb development, help unit testing etc. Do download eclipse or netbeans. Install some more databases like jboss, postgresql, mysql. For some other type of command line compilation install something like ant(like make on unix), maven2(It downloads all the jar you require from internet first time). For springframework you have to download a big archive file ( at this time spring-framework-2.5.4-with-dependencies.zip (77MB)). It has all the jar you require to develop spring apps. Even small database like hsqldb

---

### Post by szweju on 2009-04-12
I've had this same problem. I've tried to run this installation file as a super user "sudo *.bin", but when I've run this file as a normal user, everything was ok.

---

### Post by CptPicard on 2009-04-12
Just listen to tinny and get Netbeans instead (it's the only sane J2EE development environment IMO and works great). You will be developing against the application server, not some stuff you download separately from Sun.

---

### Post by illuminatifire on 2009-10-07
There's a download that installs the eclipse IDE , it's prepackaged by sun, it comes J2EE ready and its a different IDE than netbeans. This is a quick way of installing J2EE without having to deal with other files.  Do a search for glassfish and eclipse.  This download can be found at the SUN glassfish site. Here's the link [http://download.java.net/glassfish/eclipse/](http://download.java.net/glassfish/eclipse/)

---

