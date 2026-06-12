---
title: "NoClassDefFoundError when class is in classpath?"
date: 2006-03-15
forum: Programming Talk
---

### Post by joshuapurcell on 2006-03-15
What would the reasons be for getting a java.lang.NoClassDefFoundError if you are certain you have the needed class listed in your classpath? I'm trying to run a bash script that starts a java process which calls a web service, but I keep getting an error saying a class definition that is in webservices.jar is not found.

Here's the first part of the java command (minus the arguments for the AddMeasurement web service):```
java -cp webservices.jar:ffdc.jar:wsdl4j.jar:ras.jar:bootstrap.jar:emf.jar:wsexception.jar:j2ee.jar:ESBCommon.jar:ESBClient.jar com.ibmsoa.client.driver.AddMeasurement
```
As you can see, my classpath includes webservices.jar, which includes com.ibm.ws.webservices.engine.components.logger.LogFactory:```
# for file in *.jar; do echo "$file" && unzip -l "$file" | grep LogFactory; done
bootstrap.jar
emf.jar
ESBClient.jar
ESBCommon.jar
ffdc.jar
j2ee.jar
ras.jar
webservices.jar
      935  11-05-04 12:09   com/ibm/ws/webservices/engine/components/logger/LogFactory$1.class
     1364  11-05-04 12:09   com/ibm/ws/webservices/engine/components/logger/LogFactory.class
wsdl4j.jar
wsexception.jar
```

But I'm getting this error:```
Exception in thread "main" java.lang.NoClassDefFoundError: com/ibm/ws/webservices/engine/components/logger/LogFactory
```

Any ideas?

---

### Post by psuresh246 on 2006-08-29
Hi,
   Give the directory path of host machine webservices.jar in classpath.

---

### Post by chonger on 2006-08-29
A complicated answer is that there a custom classloader that does not have the same classpath as the system classpath (what you specified on the command line).

I see you are using a bash script to verify that the class you are looking for is in the classpath. How about using this command to try to run the class you are looking for? It is a better way:

```

java -cp webservices.jar:ffdc.jar:wsdl4j.jar:ras.jar:bootstrap.jar:emf.jar:wsexception.jar:j2ee.jar:ESBCommon.jar:ESBClient.jar  com.ibm.ws.webservices.engine.components.logger.LogFactory 

```

Note that it is asking the JVM to initialize the LogFactory class and execute its static main(argv[]) method. You should get the following error message if the class *is* in your classpath:

Exception in thread "main" java.lang.NoSuchMethodError: main

---

