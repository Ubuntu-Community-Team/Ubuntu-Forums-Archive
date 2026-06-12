---
title: "Spring book code: Error-need help"
date: 2009-09-13
forum: Programming Talk
---

### Post by andrew222 on 2009-09-13
Hello,

I am trying to run a program from the source code for the book "Spring Into Action".  The program is from ch. 1 and we can download the code from [www.manning/walls3](www.manning/walls3)

The code is basically an example of using dependency injection.
 
I recreated the package structure
I added the .xml config files 
I included the spring.jar file

I am not getting any 'red block' errors from Eclipse. 


When I compile the code, I get a NoClassDefFoundError with this additional output

> 
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory
	at org.springframework.util.ClassUtils.<clinit>(ClassUtils.java:72)
	at org.springframework.core.io.DefaultResourceLoader.<init>(DefaultResourceLoader.java:52)
	at org.springframework.context.support.AbstractApplicationContext.<init>(AbstractApplicationContext.java:184)
	at org.springframework.context.support.AbstractRefreshableApplicationContext.<init>(AbstractRefreshableApplicationContext.java:80)
	at org.springframework.context.support.AbstractXmlApplicationContext.<init>(AbstractXmlApplicationContext.java:58)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:119)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:66)
	at com.springinaction.chapter01.knight.KnightApp.main(KnightApp.java:9)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.logging.LogFactory
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 8 more


What could I be doing wrong? 
What things should i try?


any help is welcome!

---

### Post by myrtle1908 on 2009-09-13
You are lacking the Apache Commons Logging package.  Download it here [http://commons.apache.org/logging/guide.html](http://commons.apache.org/logging/guide.html)

---

### Post by andrew222 on 2009-09-13
Thank you for that advice, that worked.  

I downloaded and added the jar...

I now have a new Error, as seen below and I suspect it may have something to do with AspectJ...


> 
log4j:WARN No appenders could be found for logger (org.springframework.context.support.ClassPathXmlApplicationContext).
log4j:WARN Please initialize the log4j system properly.
Exception in thread "main" org.springframework.beans.factory.BeanDefinitionStoreException: Unexpected exception parsing XML document from class path resource [com/springinaction/chapter01/knight/knight.xml]; nested exception is java.lang.NoClassDefFoundError: org/aspectj/lang/JoinPoint
Caused by: java.lang.NoClassDefFoundError: org/aspectj/lang/JoinPoint
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:169)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.class$(ConfigBeanDefinitionParser.java:206)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.getAdviceClass(ConfigBeanDefinitionParser.java:425)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.createAdviceDefinition(ConfigBeanDefinitionParser.java:379)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.parseAdvice(ConfigBeanDefinitionParser.java:346)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.parseAspect(ConfigBeanDefinitionParser.java:256)
	at org.springframework.aop.config.ConfigBeanDefinitionParser.parse(ConfigBeanDefinitionParser.java:146)
	at org.springframework.beans.factory.xml.NamespaceHandlerSupport.parse(NamespaceHandlerSupport.java:69)
	at org.springframework.beans.factory.xml.BeanDefinitionParserDelegate.parseCustomElement(BeanDefinitionParserDelegate.java:1123)
	at org.springframework.beans.factory.xml.BeanDefinitionParserDelegate.parseCustomElement(BeanDefinitionParserDelegate.java:1113)
	at org.springframework.beans.factory.xml.DefaultBeanDefinitionDocumentReader.parseBeanDefinitions(DefaultBeanDefinitionDocumentReader.java:133)
	at org.springframework.beans.factory.xml.DefaultBeanDefinitionDocumentReader.registerBeanDefinitions(DefaultBeanDefinitionDocumentReader.java:90)
	at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.registerBeanDefinitions(XmlBeanDefinitionReader.java:468)
	at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.doLoadBeanDefinitions(XmlBeanDefinitionReader.java:363)
	at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBeanDefinitions(XmlBeanDefinitionReader.java:313)
	at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBeanDefinitions(XmlBeanDefinitionReader.java:290)
	at org.springframework.beans.factory.support.AbstractBeanDefinitionReader.loadBeanDefinitions(AbstractBeanDefinitionReader.java:131)
	at org.springframework.beans.factory.support.AbstractBeanDefinitionReader.loadBeanDefinitions(AbstractBeanDefinitionReader.java:147)
	at org.springframework.beans.factory.support.AbstractBeanDefinitionReader.loadBeanDefinitions(AbstractBeanDefinitionReader.java:173)
	at org.springframework.context.support.AbstractXmlApplicationContext.loadBeanDefinitions(AbstractXmlApplicationContext.java:112)
	at org.springframework.context.support.AbstractXmlApplicationContext.loadBeanDefinitions(AbstractXmlApplicationContext.java:79)
	at org.springframework.context.support.AbstractRefreshableApplicationContext.refreshBeanFactory(AbstractRefreshableApplicationContext.java:101)
	at org.springframework.context.support.AbstractApplicationContext.obtainFreshBeanFactory(AbstractApplicationContext.java:394)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:324)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:122)
	at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:66)
	at com.springinaction.chapter01.knight.KnightApp.main(KnightApp.java:9)
Caused by: java.lang.ClassNotFoundException: org.aspectj.lang.JoinPoint
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 28 more
 


Is there anything I have done wrong?
are there any API's missing?

The Eclipse project file of this app is attached to this thread as well....

Any help is welcome...

---

### Post by myrtle1908 on 2009-09-13
I know nothing about Spring or AspectJ but whenever you get

```
java.lang.NoClassDefFoundError
```

in a Java compile it is because you are lacking some required library.  In your case, the compiler cannot find the org/aspectj/lang/JoinPoint class.

Try the findjar site.  [http://www.findjar.com/class/org/aspectj/lang/JoinPoint.html](http://www.findjar.com/class/org/aspectj/lang/JoinPoint.html)

---

### Post by andrew222 on 2009-09-13
Thank you, I did not know about this site...This solved the problem.  It runs with no errors/exceptions...

---

