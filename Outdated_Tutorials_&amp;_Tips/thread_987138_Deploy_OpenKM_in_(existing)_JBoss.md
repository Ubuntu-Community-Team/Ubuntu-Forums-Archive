---
title: "Deploy OpenKM in (existing) JBoss"
date: 2008-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by FrankSpierings on 2008-11-19
This tutorial will show you how to setup the current OpenKM DMS in Ubuntu (8.10). 
OpenKM is currently bundled with JBoss, but some of us like to deploy such software in an existing environment.

I will first show how to install JBoss. 

NOTE: You could also try to install JBoss including init.d script according to the following tutorial: [http://ubuntuforums.org/showthread.php?p=4031613](http://ubuntuforums.org/showthread.php?p=4031613)

Make sure you have a root shell!
```

#Install Sun Java 5 JDK
apt-get install sun-java5-jdk

#Create temp download directory
mkdir /tmp/download

#Change to temp download directory
cd /tmp/download

#Get the JBoss source file
wget http://heanet.dl.sourceforge.net/sourceforge/jboss/jboss-4.2.3.GA.zip

#Install unzip
apt-get install unzip

#Unzip JBoss
unzip jboss-4.2.3.GA.zip

#Change directory to unzipped JBoss
cd jboss-4.2.3.GA

#Create JBoss system directory. You could change this.
export JBOSS=/opt/JBoss-4.2.3 
mkdir $JBOSS

#Copy JBoss source to system directory
cp -R * $JBOSS

#Check if JBoss can start
$JBOSS/bin/run.sh -b 0.0.0.0
```

You should get the following (similar) output on the console.
Also check if you can reach the JBoss server http://<IP>:8080
Stop the server by pressing CTRL+C
> 
=========================================================================

  JBoss Bootstrap Environment

  JBOSS_HOME: /opt/JBoss-4.2.3

  JAVA: java

  JAVA_OPTS: -Dprogram.name=run.sh -server -Xms128m -Xmx512m -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -Djava.net.preferIPv4Stack=true

  CLASSPATH: /opt/JBoss-4.2.3/bin/run.jar

=========================================================================

12:35:27,524 INFO  [Server] Starting JBoss (MX MicroKernel)...
12:35:27,525 INFO  [Server] Release ID: JBoss [Trinity] 4.2.3.GA (build: SVNTag=JBoss_4_2_3_GA date=200807181417)
12:35:27,526 INFO  [Server] Home Dir: /opt/JBoss-4.2.3
12:35:27,526 INFO  [Server] Home URL: file:/opt/JBoss-4.2.3/
12:35:27,527 INFO  [Server] Patch URL: null
12:35:27,527 INFO  [Server] Server Name: default
12:35:27,527 INFO  [Server] Server Home Dir: /opt/JBoss-4.2.3/server/default
12:35:27,528 INFO  [Server] Server Home URL: file:/opt/JBoss-4.2.3/server/default/
12:35:27,528 INFO  [Server] Server Log Dir: /opt/JBoss-4.2.3/server/default/log
12:35:27,528 INFO  [Server] Server Temp Dir: /opt/JBoss-4.2.3/server/default/tmp
12:35:27,529 INFO  [Server] Root Deployment Filename: jboss-service.xml
12:35:27,756 INFO  [ServerInfo] Java version: 1.5.0_16,Sun Microsystems Inc.
12:35:27,756 INFO  [ServerInfo] Java VM: Java HotSpot(TM) Server VM 1.5.0_16-b02,Sun Microsystems Inc.
12:35:27,756 INFO  [ServerInfo] OS-System: Linux 2.6.27-7-server,i386
12:35:28,201 INFO  [Server] Core system initialized
12:35:30,587 INFO  [WebService] Using RMI server codebase: [http://ubuntu.localdomain:8083/](http://ubuntu.localdomain:8083/)
12:35:30,589 INFO  [Log4jService$URLWatchTimerTask] Configuring from URL: resource:jboss-log4j.xml
12:35:31,356 INFO  [TransactionManagerService] JBossTS Transaction Service (JTA version) - JBoss Inc.
12:35:31,357 INFO  [TransactionManagerService] Setting up property manager MBean and JMX layer
12:35:31,650 INFO  [TransactionManagerService] Starting recovery manager
12:35:31,804 INFO  [TransactionManagerService] Recovery manager started
12:35:31,812 INFO  [TransactionManagerService] Binding TransactionManager JNDI Reference
12:35:36,089 INFO  [EJB3Deployer] Starting java:comp multiplexer
12:35:38,912 INFO  [NativeServerConfig] JBoss Web Services - Native
12:35:38,913 INFO  [NativeServerConfig] jbossws-3.0.1-native-2.0.4.GA (build=200803312044)
12:35:40,106 INFO  [Embedded] Catalina naming disabled
12:35:40,202 INFO  [AprLifecycleListener] The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server:/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386:/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/../lib/i386
12:35:40,328 INFO  [Http11Protocol] Initializing Coyote HTTP/1.1 on http-0.0.0.0-8080
12:35:40,346 INFO  [AjpProtocol] Initializing Coyote AJP/1.3 on ajp-0.0.0.0-8009
12:35:40,346 INFO  [Catalina] Initialization processed in 239 ms
12:35:40,346 INFO  [StandardService] Starting service jboss.web
12:35:40,348 INFO  [StandardEngine] Starting Servlet Engine: JBossWeb/2.0.1.GA
12:35:40,430 INFO  [Catalina] Server startup in 83 ms
12:35:40,493 INFO  [TomcatDeployer] deploy, ctxPath=/, warUrl=.../deploy/jboss-web.deployer/ROOT.war/
12:35:41,294 INFO  [TomcatDeployer] deploy, ctxPath=/invoker, warUrl=.../deploy/http-invoker.sar/invoker.war/
12:35:41,567 INFO  [TomcatDeployer] deploy, ctxPath=/jbossws, warUrl=.../deploy/jbossws.sar/jbossws-context.war/
12:35:41,716 INFO  [TomcatDeployer] deploy, ctxPath=/jbossmq-httpil, warUrl=.../deploy/jms/jbossmq-httpil.sar/jbossmq-httpil.war/
12:35:42,879 INFO  [TomcatDeployer] deploy, ctxPath=/web-console, warUrl=.../deploy/management/console-mgr.sar/web-console.war/
12:35:43,646 INFO  [MailService] Mail Service bound to java:/Mail
12:35:43,878 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/jboss-ha-local-jdbc.rar
12:35:43,932 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/jboss-ha-xa-jdbc.rar
12:35:43,976 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/jboss-local-jdbc.rar
12:35:44,023 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/jboss-xa-jdbc.rar
12:35:44,113 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/jms/jms-ra.rar
12:35:44,158 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/mail-ra.rar
12:35:44,227 INFO  [RARDeployment] Required license terms exist, view META-INF/ra.xml in .../deploy/quartz-ra.rar
12:35:44,240 INFO  [QuartzResourceAdapter] start quartz!!!
12:35:44,362 INFO  [SimpleThreadPool] Job execution threads will use class loader of thread: main
12:35:44,572 INFO  [QuartzScheduler] Quartz Scheduler v.1.5.2 created.
12:35:44,581 INFO  [RAMJobStore] RAMJobStore initialized.
12:35:44,589 INFO  [StdSchedulerFactory] Quartz scheduler 'DefaultQuartzScheduler' initialized from default resource file in Quartz package: 'quartz.properties'
12:35:44,590 INFO  [StdSchedulerFactory] Quartz scheduler version: 1.5.2
12:35:44,590 INFO  [QuartzScheduler] Scheduler DefaultQuartzScheduler_$_NON_CLUSTERED started.
12:35:45,803 INFO  [ConnectionFactoryBindingService] Bound ConnectionManager 'jboss.jca:service=DataSourceBinding,name=DefaultDS' to JNDI name 'java:DefaultDS'
12:35:46,353 INFO  [A] Bound to JNDI name: queue/A
12:35:46,370 INFO  [B] Bound to JNDI name: queue/B
12:35:46,371 INFO  [C] Bound to JNDI name: queue/C
12:35:46,372 INFO  [D] Bound to JNDI name: queue/D
12:35:46,374 INFO  [ex] Bound to JNDI name: queue/ex
12:35:46,415 INFO  [testTopic] Bound to JNDI name: topic/testTopic
12:35:46,416 INFO  [securedTopic] Bound to JNDI name: topic/securedTopic
12:35:46,423 INFO  [testDurableTopic] Bound to JNDI name: topic/testDurableTopic
12:35:46,427 INFO  [testQueue] Bound to JNDI name: queue/testQueue
12:35:46,511 INFO  [UILServerILService] JBossMQ UIL service available at : /0.0.0.0:8093
12:35:46,594 INFO  [DLQ] Bound to JNDI name: queue/DLQ
12:35:46,812 INFO  [ConnectionFactoryBindingService] Bound ConnectionManager 'jboss.jca:service=ConnectionFactoryBinding,name=JmsXA' to JNDI name 'java:JmsXA'
12:35:46,859 INFO  [TomcatDeployer] deploy, ctxPath=/jmx-console, warUrl=.../deploy/jmx-console.war/
12:35:47,134 INFO  [Http11Protocol] Starting Coyote HTTP/1.1 on http-0.0.0.0-8080
12:35:47,189 INFO  [AjpProtocol] Starting Coyote AJP/1.3 on ajp-0.0.0.0-8009
12:35:47,227 INFO  [Server] JBoss (MX MicroKernel) [4.2.3.GA (build: SVNTag=JBoss_4_2_3_GA date=200807181417)] Started in 19s:697ms


After you have verified the JBoss installation, you can continue with the deployment of the OpenKM.

```

#Define the location of JBoss in (temp) env. variable. 
#Change this if your location is different!
export JBOSS=/opt/JBoss-4.2.3

#Create temp download directory. Only needed if it does not exist already.
mkdir /tmp/download

#Change to temp download directory
cd /tmp/download

#Get the bundled OpenKM source. Note that I could not find other downloads for OpenKM.
wget http://surfnet.dl.sourceforge.net/sourceforge/openkm/OpenKM-3.0-RC2_JBoss-4.2.2.GA.zip

#Install unzip
apt-get install unzip

#Unzip OpenKM
unzip OpenKM-3.0-RC2_JBoss-4.2.2.GA.zip

#Change to the OpenMK source directory
cd OpenKM-3.0-RC2_JBoss-4.2.2.GA

#The following files are required for the correct deployment of OpenKM.
cp PropertyGroupBundle.properties $JBOSS
cp PropertyGroupValues.properties $JBOSS
cp repository.xml $JBOSS

#The actual deployment files for OpenMK can now be copied.
cp server/default/deploy/openkm-ds.xml $JBOSS/server/default/deploy
cp server/default/deploy/OpenKM.ear $JBOSS/server/default/deploy

```

You should now be able to successfully start JBoss again. It should deploy OpenKM correctly, BUT you will not be able to login. 

To fix this open file: *$JBOSS/server/default/conf/login-config.xml*

Insert the following text just before **</policy>**

```

    <!-- OpenKM -->
    <application-policy name = "OpenKM">
      <authentication>
        <login-module code="org.jboss.security.auth.spi.DatabaseServerLoginModule" flag = "required">
          <module-option name="dsJndiName">java:/OKMAuthDS</module-option>
          <module-option name="principalsQuery">select usr_pass as PASSWD from users where usr_id=? and usr_active='true'</module-option>
          <module-option name="rolesQuery">select ur_role as ROLEID, 'Roles' from user_role where ur_user=?</module-option>
        </login-module>
      </authentication>
    </application-policy>

```

You can now login to http://<IP>:8080/OpenKM with username/password admin/admin

---

### Post by guber112 on 2009-01-30
I have a security question about JBoss. How would I keep people from seeing the "http://localhost:8080" (main page of JBoss)? What are security check that I need to do in order to secure it? Thanks.

---

### Post by all4tux on 2009-02-17
hello and many thanks for the how to. one thing though, what is the user name and password to use. i have tried admin admin, ubuntu user, root and non of them work. what is the user and password to log in.  many thanks

---

### Post by pieterbezuijen on 2010-03-17
> **guber112 said:**
> I have a security question about JBoss. How would I keep people from seeing the "http://localhost:8080" (main page of JBoss)? What are security check that I need to do in order to secure it? Thanks.

I found a 'Getting Started Guide' on [https://community.jboss.org/wiki/JBossapplicationserverofficialdocumentationpage](https://community.jboss.org/wiki/JBossapplicationserverofficialdocumentationpage). At page 18 there is some basic information about security. I don't know how to secure the main page, but in the guide is  written how to secure some vital parts of this page.

---

