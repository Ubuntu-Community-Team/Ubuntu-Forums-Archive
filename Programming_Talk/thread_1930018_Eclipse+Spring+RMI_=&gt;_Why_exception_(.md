---
title: "Eclipse+Spring+RMI =&gt; Why exception?? :("
date: 2012-02-22
forum: Programming Talk
---

### Post by c2tarun on 2012-02-22
[INDENT]Hi friends,
 
I am trying to implement the example on page: [http://codetojoy.blogspot.in/2007/12/zero-to-rmi-in-minutes-or-i-heart.html](http://codetojoy.blogspot.in/2007/12/zero-to-rmi-in-minutes-or-i-heart.html)
in RAD(eclipse). I am able to Run the server program properly but when I am trying to run the client program I am getting BeanCreationException when trying to inject RmiProxyFactoryBean object.
 
Here are the service side classes:
```

package com.service;
public class MathServiceImpl implements MathService {
 @Override
 public int add(int a, int b) {
  // TODO Auto-generated method stub
  return a+b;
 }
 @Override
 public int pro(int a, int b) {
  // TODO Auto-generated method stub
  return a*b;
 }
}

```
 
```

package com.service;
import org.springframework.context.ApplicationContext;
public class MathServiceStart {
 public static void main(String[] args) {
  try {
   ApplicationContext ctx = new ClassPathXmlApplicationContext(
     "MathService.xml");
  } catch (Exception e) {
   System.out.println("Inside catch");
   e.printStackTrace();
  }
 }
}

```
Service XML (MathService.xml)
```

 <bean id="mathService" class="com.service.MathServiceImpl" />
 <bean
  class="org.springframework.remoting.rmi.RmiServiceExporter">
 
  <property name="serviceName" value="MathService"/>
  <property name="service" ref="mathService"/>
  <property name="serviceInterface" value="com.service.MathService"/>
  <property name="registryPort" value="9911"/>
 </bean>

```
CLIENT side codes
```

package com.math.caller;
 
public class MathCaller {
 
 private MathService ms;
 public MathService getMs() {
  return ms;
 }
 public void setMs(MathService ms) {
  this.ms = ms;
 }
 
 public void add() {
  System.out.println(ms.add(10, 20));
 }
 
 public void pro() {
  System.out.println(ms.pro(5, 25));
 }
 
}

```
```

package com.math.caller;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
public class MathCallerClient {
 
 public static void main(String[] args) {
  ApplicationContext bf = new ClassPathXmlApplicationContext("client.xml");
  MathCaller mc = (MathCaller) bf.getBean("mathCaller");
 
  mc.add();
  mc.pro();
 }
}

```
 
Client side XML
```

 <bean id="MathService"
  class="org.springframework.remoting.rmi.RmiProxyFactoryBean">
 
  <property name="serviceUrl" value="rmi://localhost:9911/MathService"/>
  <property name="serviceInerface" value="com.math.caller.MathService"></property>
 </bean>
 <bean id="mathCaller" class="com.math.caller.MathCaller">
  <property name="ms" ref="MathService" />
 </bean>

```
When I am executing MathServiceStart class I am getting no error or exception. But when I am executing to access the RMI service I am getting the following exception.
 
```

23 Feb, 2012 7:39:25 AM org.springframework.context.support.AbstractApplicationContext prepareRefresh
INFO: Refreshing org.springframework.context.support.ClassPathXmlApplicationContext@61b383e9: display name [org.springframework.context.support.ClassPathXmlApplicationContext@61b383e9]; startup date [Thu Feb 23 07:39:25 IST 2012]; root of context hierarchy
23 Feb, 2012 7:39:25 AM org.springframework.beans.factory.xml.XmlBeanDefinitionReader loadBeanDefinitions
INFO: Loading XML bean definitions from class path resource [client.xml]
23 Feb, 2012 7:39:25 AM org.springframework.context.support.AbstractApplicationContext obtainFreshBeanFactory
INFO: Bean factory for application context [org.springframework.context.support.ClassPathXmlApplicationContext@61b383e9]: org.springframework.beans.factory.support.DefaultListableBeanFactory@651dba45
23 Feb, 2012 7:39:25 AM org.springframework.beans.factory.support.DefaultListableBeanFactory preInstantiateSingletons
INFO: Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@651dba45: defining beans [MathService,mathCaller]; root of factory hierarchy
23 Feb, 2012 7:39:25 AM org.springframework.beans.factory.support.DefaultSingletonBeanRegistry destroySingletons
INFO: Destroying singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@651dba45: defining beans [MathService,mathCaller]; root of factory hierarchy
Exception in thread "main" org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'MathService' defined in class path resource [client.xml]: Error setting property values; nested exception is org.springframework.beans.NotWritablePropertyException: Invalid property 'serviceInerface' of bean class [org.springframework.remoting.rmi.RmiProxyFactoryBean]: Bean property 'serviceInerface' is not writable or has an invalid setter method. Did you mean 'serviceInterface'?
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1279)
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
 at java.security.AccessController.doPrivileged(Native Method)
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
 at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
 at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
 at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
 at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
 at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
 at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:423)
 at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:728)
 at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:380)
 at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:139)
 at org.springframework.context.support.ClassPathXmlApplicationContext.<init>(ClassPathXmlApplicationContext.java:83)
 at com.math.caller.MathCallerClient.main(MathCallerClient.java:9)
Caused by: org.springframework.beans.NotWritablePropertyException: Invalid property 'serviceInerface' of bean class [org.springframework.remoting.rmi.RmiProxyFactoryBean]: Bean property 'serviceInerface' is not writable or has an invalid setter method. Did you mean 'serviceInterface'?
 at org.springframework.beans.BeanWrapperImpl.setPropertyValue(BeanWrapperImpl.java:801)
 at org.springframework.beans.BeanWrapperImpl.setPropertyValue(BeanWrapperImpl.java:651)
 at org.springframework.beans.AbstractPropertyAccessor.setPropertyValues(AbstractPropertyAccessor.java:78)
 at org.springframework.beans.AbstractPropertyAccessor.setPropertyValues(AbstractPropertyAccessor.java:59)
 at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1276)
 ... 16 more
```
 
Following are my file structures for Client [ATTACH]213132[/ATTACH]
 
Service [ATTACH]213133[/ATTACH]
 
Can anyone please help?
[/INDENT]

---

### Post by c2tarun on 2012-02-23
I think I found the mistake, I should put the service's interface in the same package in the client project. I'll go home and give it a try. 
 
Any other suggestions are welcome. If it'll work I'll close this thread.

---

### Post by c2tarun on 2012-02-23
..

---

### Post by r-senior on 2012-02-23
Are you sure it's not related to this:

```
Bean property 'serviceInerface' is not writable or has an invalid setter method. Did you mean 'serviceInterface'?
```

---

