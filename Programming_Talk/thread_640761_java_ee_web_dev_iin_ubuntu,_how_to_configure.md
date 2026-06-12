---
title: "java ee web dev iin ubuntu, how to configure"
date: 2007-12-14
forum: Programming Talk
---

### Post by cuco2772 on 2007-12-14
I am using  ubuntu(feisty) and want  to be able to do jsp/servlet
web development. I have manually downloaded and installed
the tomcat web container, eclipse europa, and this bin file from the
Sun site here :

 [http://java.sun.com/javaee/downloads/index.jsp](http://java.sun.com/javaee/downloads/index.jsp)

I downloaded the java_ee_sdk-5_03-linux.bin file, the SDK with jdk
one, and installed it in /opt. .It extracted into a directory called /SDK.

I had previously installed sun-java5 using apt-get, which installed it in
/usr/lib. The problem I'm having now is I cant get the system to recognize the new Java, even though I have reset the $JAVA_HOME to point to the new installation. If I use update-alternatives --config java,
only the version 1.5 and gcj comes up.  Right now, if I try compile  a HelloServlet.java servlet (located in WEB-INF dir.,, for those of you familiar with tomcat),
I get the 'javax.servlet package does not exist error'.  My javac 1.5 version gets invoked, which doesnt know where to load those classes.

Has anybody setup their computer to do java ee web development ?
If you could tell me the steps you took to get it working, that would
be extremely helpful. I have my tomcat up and running in /usr/local.
The tomcat home page comes up when I access localhost:8080, so 
I know that works. Thanks.

---

### Post by staticvoid on 2007-12-14
Have you tried just installing it clean from synaptic? and why not java6 update 3?

just search for "sun-" and install the jdk and jre.

Can't help you with the ee stuff. I just use geany with a button to compile and execute. When I install from synaptic I did not have probs with linking and stuff.

I hit javac and it found the java folder


good luck
sv

---

### Post by cuco2772 on 2007-12-14
> **staticvoid said:**
> Have you tried just installing it clean from synaptic? and why not java6 update 3?

just search for "sun-" and install the jdk and jre.

Can't help you with the ee stuff. I just use geany with a button to compile and execute. When I install from synaptic I did not have probs with linking and stuff.

I hit javac and it found the java folder


good luck
sv

Thanks, I wish it were that simple. It seems like in order to get the ee stuff, you have to do it manually, I'm not aware of any apt-get that will do that.

I tried doing this: I did an apt-get javapackage,  which included
fakeroot.  Then I tried doing fakeroot make-jpkg the-bin-file that I
downloaded from the sun site.  It almost  worked. There was one 
missing plugin. That would have created a .deb package which I
would have been able to install with Synaptic, I think.

---

### Post by jespdj on 2007-12-16
You do not need the Java EE SDK to do Java EE development.

First, make sure you install the latest Java SE from Sun from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```
This should make Sun Java 1.6.0_03 your current Java version (check after installing with "java -version").

To develop Java EE programs, you'll need an application server. Get [GlassFish]("https://glassfish.dev.java.net/"), which is Sun's open source Java EE application server. GlassFish version 2 is the current release version.

To compile your Java EE source that uses the Java EE API classes and interfaces, include **javaee.jar** which you can find in the **lib** directory of your GlassFish installation into the classpath.

Ofcourse, read the GlassFish documentation to learn how to run it and how to deploy your applications in it.

---

### Post by cuco2772 on 2007-12-16
> **jespdj said:**
> You do not need the Java EE SDK to do Java EE development.

First, make sure you install the latest Java SE from Sun from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```
This should make Sun Java 1.6.0_03 your current Java version (check after installing with "java -version").

To develop Java EE programs, you'll need an application server. Get [GlassFish]("https://glassfish.dev.java.net/"), which is Sun's open source Java EE application server. GlassFish version 2 is the current release version.

To compile your Java EE source that uses the Java EE API classes and interfaces, include **javaee.jar** which you can find in the **lib** directory of your GlassFish installation into the classpath.

Ofcourse, read the GlassFish documentation to learn how to run it and how to deploy your applications in it.

Thanks for the reply. I used apt-get to install sun-java6 which installs
automatically into a /usr/lib/jvm/java-6-sun-1.6.0.00.
I then downloaded this binary from Sun's Java ee downloads site:

java_ee_sdk-5_03-linux-nojdk.bin. (This is the Java ee 5 SDK with no jdk). I installed this into the same directory as the Java above.
This comes with the Sun Java Application Server which runs on port
4848 on localhost. The javaee.jar file is at
/usr/lib/jvm/java-6-sun-1.6.0.00/lib/javaee.jar.

When I did  * locate servlet.jar * I got this:

/usr/lib/jvm/java-6-sun-1.6.0.00/imq/lib/imqservlet.jar
I'm wondering if this is Ok or should it say something like
jnlp-servlet.jar ?

I did a little research and realized that the problem I'm having with
javac not finding the definition for javax.servlet package is likely
the result of the CLASSPATH not being set properly.
 Thats the one thing I dont think I did.

Where do you set your classpath and what do you want it to point
to ?  Does it have to be set separately for tomcat also ?

Do you think Sun's Application Server is sufficient or would
GLassfish work better ? 

Sorry for all the questions. The most important one is about the 
classpath if you dont have time to answer them all. Thanks again.

---

### Post by jespdj on 2007-12-18
> **cuco2772 said:**
> java_ee_sdk-5_03-linux-nojdk.bin. (This is the Java ee 5 SDK with no jdk). I installed this into the same directory as the Java above.
I don't think it was a good idea to extract it in your JDK directory. It's not meant to be used that way.
> When I did  * locate servlet.jar * I got this:

/usr/lib/jvm/java-6-sun-1.6.0.00/imq/lib/imqservlet.jar
I'm wondering if this is Ok or should it say something like
jnlp-servlet.jar ?

I did a little research and realized that the problem I'm having with
javac not finding the definition for javax.servlet package is likely
the result of the CLASSPATH not being set properly.
 Thats the one thing I dont think I did.
You just need to include **javaee.jar** into your classpath. It includes the servlet API classes. You don't need to find a servlet.jar or something similar.
> Where do you set your classpath and what do you want it to point
to ?  Does it have to be set separately for tomcat also ?
When you compile servlet source code, you need to include javaee.jar into the classpath like this, for example:
```
javac -classpath /usr/lib/jvm/java-6-sun-1.6.0.00/lib/javaee.jar:. MyServlet.java
```
After you've compiled your servlet and packaged it up in a WAR file, you can deploy the WAR file in GlassFish / Sun Java App Server, Tomcat or any other Java EE application server.
> Do you think Sun's Application Server is sufficient or would
GLassfish work better ?
Sun Java Application Server and GlassFish are the same thing. GlassFish is the name of the open source project, and Sun sells it with support under the name "Sun Java Application Server".

---

