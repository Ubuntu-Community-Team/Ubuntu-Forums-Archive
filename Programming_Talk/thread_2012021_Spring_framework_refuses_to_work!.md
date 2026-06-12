---
title: "Spring framework refuses to work!"
date: 2012-06-28
forum: Programming Talk
---

### Post by fallenshadow on 2012-06-28
Hi all,

Lately Spring is refusing to work and its not making any sense to me. I did look this up but the solutions just say to add the spring .jar files. (which are already present)

This is causing me much mental pain and suffering! ](*,)

Does anyone know why this is happening?

> 
SEVERE: Error configuring application listener of class org.springframework.web.context.ContextLoaderListener
java.lang.ClassNotFoundException: org.springframework.web.context.ContextLoaderListener


How does one troubleshoot this problem? 

Lastly... why is Spring such a pain in the butt?!!! :mad:

---

### Post by dwhitney67 on 2012-06-28
I'm not a Spring user, but I do know what a ClassNotFoundException is.  Check your CLASSPATH setting to ensure it references the jar file(s) that you are interested in using.

---

### Post by fallenshadow on 2012-06-28
Thanks for the reply!

My classpath is pretty empty:

[IMG]http://i46.tinypic.com/2nbx5y1.png[/IMG]

However im sure it used to always pick up my .jars from a lib folder. How can I make sure this configuration is still setup like this? (in Eclipse)

---

### Post by fallenshadow on 2012-06-28
I should probably mention that Spring works with Unit testing but not when I run Tomcat. :?

---

### Post by fallenshadow on 2012-06-28
So adding jars to the classpath doesn't do anything.

However looking at some commit history now. Looks like when I generated some beans/classes that some .jars were automatically added to my project.

Would these cause issues or conflicts with anything?

> axis.jar, commons-discovery.jar, commons-logging.jar, jaxrpc.jar, wsdl4j.jar.

Thats all I can think of at the moment. I would try removing these but im not sure are they required. :/ Note that I only used wsdl4j to generate some beans/classes. I didn't intend adding these jars to the project but it was done for me.

Advice on removing these would be welcome!

---

### Post by dwhitney67 on 2012-06-28
Tomcat is also a mystery to me too; I had an issue with it being unable to find a particular JAR file that my project depended upon, and all recommendations on the web indicated to place it in either $CATALINA_HOME/lib or $CATALINA_HOME/bin.  It turns out though, that I had to put the JAR file in my project's WEB-INF/lib directory.  The other two paths that were recommended did not work.

---

### Post by fallenshadow on 2012-06-28
As far as I understand all your .jars need to be in your /WEB-INF/lib folder. Except if you are using maven and a .pom file to manage dependencies.

Not that im an expert or anything but its just what works reliably for me. Clearly I have much to learn yet on this whole area.

---

### Post by fallenshadow on 2012-06-28
Seems I got spring to work again.

I removed the project from the tomcat server and cleaned it. Simple enough to fix my problem I guess. Maybe I shouldn't have posted here but if anything it gave me a chance to vent some of my frustration and maybe reduce my stress levels by 1%. :)

If I could just solve this warning below I would be happy today!

> 
WARNING: Unable to load class [org.apache.commons.logging.impl.SLF4JLogFactory] to check against the @HandlesTypes annotation of one or more ServletContentInitializers. 
java.lang.SecurityException: class "org.apache.commons.logging.impl.SLF4JLogFactory"'s signer information does not match signer information of other classes in the same package


I know its a warning and not stopping my app from running as such but it does annoy me seeing this when starting my app.

---

### Post by fallenshadow on 2012-06-29
I suppose I should mark this as solved since my original problem is gone! :)

Still don't like Spring too much... or maybe Tomcat is the one I should hate on.

---

### Post by r-senior on 2012-06-29
The SLF4J warning is because Spring now depends on SLF4J (from 3.0 IIRC). If you were using Maven to bring in the Spring JAR files, it would also bring in the SLF4J JARs.

To go back to the original discussion, required JARs should work in $CALALINA_HOME/lib or WEB-INF/lib. The classpath for a deployed web application includes both. JARs that you want to share across multiple web apps deployed on a single Tomcat instance can go in $CATALINA_HOME/lib.

If your project has JAR dependencies that need to go in WEB-INF/lib, they need to be copied into the WAR file or web application directory structure that you deploy. If you check your WAR file and they aren't there, you'll see the effect you describe, i.e. application works under unit test (because Eclipse build path has the JARs) but not on the server (because the server doesn't and they are not in the WAR file).

Spring projects are best built with Maven IMO. Actually, make that all Java projects. It saves so many classpath headaches. If you set your Maven project type to WAR, it does the right thing with dependency JARs. I know Maven looks complicated at first, but it saves so much time.

EDIT: Another point on Tomcat: if your web application is not marked as reloadable, e.g. in META-INF/context.xml, I don't think it rescans the classpath once it's deployed. Not a good setting for production servers but very useful on development. If you tried adding JARs to WEB-INF/lib without redeploying or reloading (you can do that from the Tomcat Manager application), it wouldn't pick the JARs up.

---

### Post by r-senior on 2012-06-29
> **fallenshadow said:**
> Lastly... why is Spring such a pain in the butt?!!! :mad:
It's not. It's building Java projects with dependencies that's a pain in the butt. That's why Maven is such a useful tool!

---

