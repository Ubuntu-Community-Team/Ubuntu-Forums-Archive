---
title: "SpringSource OSGi implementation problem..."
date: 2010-01-20
forum: Programming Talk
---

### Post by Crafty Kisses on 2010-01-20
So right now I'm implementing Spring into my OSGi bundles as we speak, so right now I have this:
```
package com.(sitename).project.hello;

public interface HelloWorld
{
public string hello();
}
```
So that's my service interface, but when I start implementing the service that's when I run into problems:
```
package com.(sitename).project.hello;

import com.(sitename).project.hello.JARPRoject;

public class HelloWorldService implements Helloworld
{
public String hello() {
 return "Hello World 1.0";
      }
}
```
Remember this is just a simple test, and it's not going as planned. Once I was done using the activator I noticed it's not implementing the "BundleActivator", that pretty much forms the OSGi framework. So for example, here's a little flowchart I made so maybe the people that are helping me can get a visual on this:
```
helloworld-web*
           &#8595;
helloworld-model
(Class)
           &#8595;
spring.osgi
           &#8595;
springframework-web
(Class)
           &#8595;
springframework-core
           &#8595;
springframework-beans
(Class)
           &#8595;
org.apache.commons*
           &#8595;
catalina.osgi
```
I've also tried locating the OSGi services through Spring-DM and still nothing:
```
<reference id="serviceBean" interface="com.(sitename).spring.osgi.JARProject"/>
```
So in conclusion I'm not sure if Spring is finding the Dynamic Modules for OSGi, or at least it doesn't look like it. Any ideas or suggestions?

---

