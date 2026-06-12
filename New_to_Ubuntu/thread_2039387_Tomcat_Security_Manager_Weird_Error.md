---
title: "Tomcat Security Manager Weird Error"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Bogdan User on 2012-08-08
Hello Everyone, 
  I have installed tomcat6 on ubuntu 11.10. When I start tomcat with security enabled i get this error:

Caused by: java.lang.RuntimeException: Error building service proxy for service 'RegistryStartup' (at org.apache.tapestry5.ioc.internal.services.RegistryStartup(Logger, List) (at RegistryStartup.java:36) via org.apache.tapestry5.ioc.services.TapestryIOCModule.bind(ServiceBinder) (at TapestryIOCModule.java:49)): Unable to locate class file for 'java.lang.Runnable' in class loader WebappClassLoader
  context:
  delegate: false
  repositories:
    /WEB-INF/classes/
----------> Parent Classloader:
org.apache.catalina.loader.StandardClassLoader@4d911540
.
        at org.apache.tapestry5.ioc.internal.ModuleImpl$4.invoke(ModuleImpl.java:327)
        at org.apache.tapestry5.ioc.internal.OperationTrackerImpl.invoke(OperationTrackerImpl.java:74)
        ... 44 more
**[COLOR=Red]Caused by: java.lang.RuntimeException: Unable to locate class file for 'java.lang.Runnable' in class loader WebappClassLoader[/COLOR]**
  context:
  delegate: false
  repositories:
    /WEB-INF/classes/
----------> Parent Classloader:
org.apache.catalina.loader.StandardClassLoader@4d911540
.
        at org.apache.tapestry5.internal.plastic.PlasticInternalUtils.readBytecodeForClass(PlasticInternalUtils.java:375)


Any idea what permission needs to be granted for this error to be resolved?

Thanks,

---

