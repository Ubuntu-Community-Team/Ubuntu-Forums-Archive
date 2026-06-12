---
title: "Java EE &amp; Webapps"
date: 2007-12-11
forum: Programming Talk
---

### Post by lowebb on 2007-12-11
Hi guys,

I'm trying to set up an environment where I can develop and deploy webapps in a Linux environment. I've tried setting up Tomcat with no luck at all. I simply couldnt get the server to start. 

Has anyone got an environment set up which I can develop and run a a Java Server environment? I use Eclipse so it would be excellent if I could get Eclipse to be involved in every step of the way

---

### Post by pmasiar on 2007-12-11
Do you have to use Java?

Scripting languages like Python/Ruby are much simpler and more nimble in web app development. Java is just to clunky IMHO. I did one app in Java/Struts and one in Python/Turbogears, I would never use Java anymore if I dont have to.

---

### Post by sgordon on 2007-12-11
lowebb.

I hear that running tomcat as a plugin to Eclipse can be more successful, although haven't tried myself, must admit.

Have you tried Glassfish? It's in the repositories, hence should be smooth to install, although Tomcat didn't go so well for you! There are plugins available if you really want a joined-up IDE: [https://glassfishplugins.dev.java.net/](https://glassfishplugins.dev.java.net/)

Webapps don't really need much to get the IDE outputting in a deployable format. I'll admit that getting the debugging setup correctly is harder, but I averse to debugging anyhow!

  Si

---

### Post by lowebb on 2007-12-11
> **sgordon said:**
> lowebb.

I hear that running tomcat as a plugin to Eclipse can be more successful, although haven't tried myself, must admit.

Have you tried Glassfish? It's in the repositories, hence should be smooth to install, although Tomcat didn't go so well for you! There are plugins available if you really want a joined-up IDE: [https://glassfishplugins.dev.java.net/](https://glassfishplugins.dev.java.net/)

Webapps don't really need much to get the IDE outputting in a deployable format. I'll admit that getting the debugging setup correctly is harder, but I averse to debugging anyhow!

  Si

I like the looks of glassfish. Thanks, I'll maybe give that a go, there seems to be ok documentation on. I'll keep the forum posted on ym progress.

---

### Post by jespdj on 2007-12-11
> **lowebb said:**
> I'm trying to set up an environment where I can develop and deploy webapps in a Linux environment. I've tried setting up Tomcat with no luck at all. I simply couldnt get the server to start.
Explain in more detail why it doesn't work. How did you install Tomcat? Which version of Java and Tomcat are you using? What happens when you try to start Tomcat? Do you get an error message?

I'm using Sun Java 6 (installed from the Ubuntu repository) and downloaded Tomcat 6.0 from [http://tomcat.apache.org](http://tomcat.apache.org)

I unpacked Tomcat in my home directory. Tomcat requires the environment variable JAVA_HOME to be set. So to start Tomcat, I do this:
```
JAVA_HOME=/usr/lib/jvm/java-6-sun; export JAVA_HOME
cd java/tomcat/bin
./startup.sh
```
Then open a browser and go to [http://localhost:8080](http://localhost:8080) to see if Tomcat is running.

---

### Post by CptPicard on 2007-12-11
I tend to prefer Netbeans for Java web app developing... the integration of everything is just so much better than on Eclipse. It's pretty much zero-configuration.

---

### Post by lowebb on 2007-12-12
> **jespdj said:**
> Explain in more detail why it doesn't work. How did you install Tomcat? Which version of Java and Tomcat are you using? What happens when you try to start Tomcat? Do you get an error message?

I've followed 2 different guides in these forums to try and get TomCat (5.5) working. I've had various issues throughout until I got to the point whereby enough was enough and came looking for an alternative.

Errors I've come across so far are, java package not available in repository (fixed), JAVA HOME not defined (fixed). The closest I got to the damn thing starting was 

```

28-Nov-2007 21:30:58 org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../lib/i386:/usr/java/packages/lib/i3 86:/lib:/usr/lib
28-Nov-2007 21:30:59 org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
28-Nov-2007 21:30:59 org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 2080 ms
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
28-Nov-2007 21:30:59 org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
28-Nov-2007 21:30:59 org.apache.jk.common.ChannelSocket init
INFO: Port busy 8009 java.net.BindException: Address already in use
28-Nov-2007 21:30:59 org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8010
28-Nov-2007 21:31:00 org.apache.jk.server.JkMain start
INFO: Jk running ID=1 time=0/227 config=null
28-Nov-2007 21:31:00 org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
28-Nov-2007 21:31:00 org.apache.catalina.startup.Catalina start
INFO: Server startup in 1093 ms
```

But since then I've tried again and it simply wouldnt get this far. Firing a different 1 line error (cant remmber what it was, will check up later)

The method you've described of installing it is different from any way I've tried so I may give it a go as well. To be honest, it shouldnt be this hard which puts Tomcat in a poor light in my view

---

