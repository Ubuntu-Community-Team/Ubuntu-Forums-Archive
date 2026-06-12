---
title: "Eclipse with Tomcat 7 on Ubuntu v11.10"
date: 2012-04-09
forum: Programming Talk
---

### Post by prsdrane on 2012-04-09
HI, 
      I have installed Ubuntu 11.10 on my system. I have installed  eclipse indigo,eclipse Ganymede on the same. Problem lies with tomcat  execution on eclipse indigo. I followed below steps from a blog which  help me configure tomcat7 on eclipse indigo. The problem occurs when i  execute [http://localhost:8080/](http://localhost:8080/) in browser. It displays  
  
 Error displayed in browser: 
  
 [http://localhost:8080/](http://localhost:8080/) 
  
 [B]HTTP Status 404 - / 
 type Status report 
 message / 
 description The requested resource (/) is not available. 
 Apache Tomcat/7.0.21 
 [/B] 
  
  
  
  
 **Below Steps followed for tomcat installation:** 
  
 Eclipse with Tomcat V7.0 in Ubuntu 11.10 
 1. Download Eclipse from the Eclipse web site. ([J2EE]("http://www.coderanch.com/forums/f-11/EJB-JEE") version) 
 2. Download Tomcat version 7 or install it via apt-get 
 apt-get install tomcat7 tomcat7-admin tomcat7-common tomcat7-docs tomcat7-examples 
 3. Set the following configuration: 
 cd /usr/share/tomcat7 
 sudo ln -s /var/lib/tomcat7/conf conf 
 sudo ln -s /etc/tomcat7/policy.d/03catalina.policy conf/catalina.policy 
 sudo ln -s /var/log/tomcat7 logs 
 sudo chmod -R 777 /usr/share/tomcat7/conf 
  
 3. Run eclipse 
 4. Add a view ( Windows -> Show View -> Other -> Server -> Servers -> OK ) 
 5. Go to the view 
 6. Add a Tomcat v7 (consider /user/share/tomcat7 as your path) 
 7. Enjoy Tomcat 7 in Eclipse. 
  
 **In the logs it shows as below:** 
 abc@abc-G41MT-S2P:/usr/share/tomcat7/logs$ cat localhost.2012-04-10.log 
 Apr 10, 2012 1:40:51 AM org.apache.catalina.core.ApplicationContext log 
 INFO: ContextListener: contextInitialized() 
 Apr 10, 2012 1:40:51 AM org.apache.catalina.core.ApplicationContext log 
 INFO: SessionListener: contextInitialized() 
 Apr 10, 2012 1:40:51 AM org.apache.catalina.core.ApplicationContext log 
 INFO: ContextListener:  attributeAdded('org.apache.jasper.compiler.TldLocationsCache',  'org.apache.jasper.compiler.TldLocationsCache@b52a28') 
 Apr 10, 2012 1:47:25 AM org.apache.catalina.core.ApplicationContext log 
 INFO: SessionListener: contextDestroyed() 
 Apr 10, 2012 1:47:25 AM org.apache.catalina.core.ApplicationContext log 
 INFO: ContextListener: contextDestroyed() 
  
 abc@abc-G41MT-S2P:/usr/share/tomcat7/logs$ cat catalina.2012-04-10.log 
 Apr 10, 2012 1:36:49 AM org.apache.coyote.AbstractProtocol init 
 INFO: Initializing ProtocolHandler ["http-bio-8080"] 
 Apr 10, 2012 1:36:49 AM org.apache.catalina.startup.Catalina load 
 INFO: Initialization processed in 1357 ms 
 Apr 10, 2012 1:36:49 AM org.apache.catalina.core.StandardService startInternal 
 INFO: Starting service Catalina 
 Apr 10, 2012 1:36:49 AM org.apache.catalina.core.StandardEngine startInternal 
 INFO: Starting [Servlet]("http://www.coderanch.com/forums/f-7/Servlets") Engine: Apache Tomcat/7.0.21 
 Apr 10, 2012 1:36:49 AM org.apache.catalina.startup.HostConfig deployDirectory 
 INFO: Deploying web application directory ROOT 
 Apr 10, 2012 1:36:50 AM org.apache.coyote.AbstractProtocol start 
 INFO: Starting ProtocolHandler ["http-bio-8080"] 
 Apr 10, 2012 1:36:50 AM org.apache.catalina.startup.Catalina start 
 INFO: Server startup in 1722 ms 
 Apr 10, 2012 1:38:40 AM org.apache.catalina.startup.HostConfig deployDescriptor 
 INFO: Deploying configuration descriptor manager.xml from /etc/tomcat7/Catalina/localhost 
 Apr 10, 2012 1:38:41 AM org.apache.catalina.startup.HostConfig deployDescriptor 
 INFO: Deploying configuration descriptor host-manager.xml from /etc/tomcat7/Catalina/localhost 
 Apr 10, 2012 1:40:11 AM org.apache.catalina.startup.HostConfig deployDescriptor 
 INFO: Deploying configuration descriptor docs.xml from /etc/tomcat7/Catalina/localhost 
 Apr 10, 2012 1:40:51 AM org.apache.catalina.startup.HostConfig deployDescriptor 
 INFO: Deploying configuration descriptor examples.xml from /etc/tomcat7/Catalina/localhost 
 Apr 10, 2012 1:47:24 AM org.apache.catalina.core.StandardServer await 
 INFO: A valid shutdown command was received via the shutdown port. Stopping the Server instance. 
 Apr 10, 2012 1:47:24 AM org.apache.coyote.AbstractProtocol pause 
 INFO: Pausing ProtocolHandler ["http-bio-8080"] 
 Apr 10, 2012 1:47:25 AM org.apache.catalina.core.StandardService stopInternal 
 INFO: Stopping service Catalina 
 Apr 10, 2012 1:47:25 AM org.apache.coyote.AbstractProtocol stop 
 INFO: Stopping ProtocolHandler ["http-bio-8080"] 
 Apr 10, 2012 1:47:25 AM org.apache.coyote.AbstractProtocol destroy 
 INFO: Destroying ProtocolHandler ["http-bio-8080"] 
  
  
  
 Please help me resolve this issue. 
  
  
 Thanks,

---

### Post by r-senior on 2012-04-09
When a tutorial suggests doing this ...

```
[COLOR="Red"]**sudo chmod -R 777**[/COLOR] ...
```

... you have to suspect something isn't quite right.

Installing Tomcat from the repositories is great for a server but doesn't work too well for development IME. You want Eclipse to control Tomcat and have everything where it expects it to be.

Try these instructions to install Tomcat, then set it up in Eclipse as a server. Usually works OK.

[http://ubuntuforums.org/showpost.php?p=10042855&postcount=7](http://ubuntuforums.org/showpost.php?p=10042855&postcount=7)

EDIT: It's probably moved on from 7.04 now, just get the latest from Apache.

---

### Post by pinan on 2013-01-07
you forgot to the lib and bin directories

Try

ln -s /usr/share/tomcat7/bin bin
ln -s /usr/share/tomcat7/lib lib

---

