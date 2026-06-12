---
title: "Spring Dynamic Modules (OSGi) + EclipseLink woes."
date: 2010-02-27
forum: Programming Talk
---

### Post by Crafty Kisses on 2010-02-27
So basically right now, the current code I have for the one of the DM's is:
```
<bean id="titlesConfigurer
            class="org.springframework.web.servlet.view.titles2.TilesConfigurer">
<property name ="definitions">
```
The issue is the dispatcher servlet file is not inspecting the class packages, which obviously should be inspecting these class packages. If you're wondering **MANIFEST.MF** looks something like this:
```
Manifest-Version: 1.0
Archiver-Version: Plexus Archiver
Created-By: Apache Maven
Built-By: iassan
Build-Jdk: 1.6.0_15
Export-Package: com.foo.aspect;version="2.0.0";uses:="org.aspectj.lang
 ,org.aspectj.lang.annotation,org.springframework.stereotype,com.foo.e
 xception",com.foo.exception;version="2.0.0"
Bundle-Vendor: Spring
Bundle-Version: 2.0.0
Tool: Bundlor 1.0.0.RELEASE
Bundle-Name: FooService
Import-Library: org.springframework.spring;version="[3.0.0,3.1.0)"
Bundle-ManifestVersion: 2
Bundle-SymbolicName: com.foo
Web-ContextPath: FooService
Import-Package: org.apache.log4j;version="[1.2.15,1.2.15]",org.aspectj
 .lang;version="[1.6.6.RELEASE,1.6.6.RELEASE]",org.aspectj.lang.annota
 tion;version="[1.6.6.RELEASE,1.6.6.RELEASE]",org.springframework.cont
 ext.config;version="[3.0.0,3.1.0)",org.springframework.stereotype;ver
 sion="[3.0.0,3.1.0)"
```
I also tried making it show the complete contents, by running:
```
jinspect -D Bundle-ClassPath mybundle.jar
```
I then try to start my RCP and I get the following:
```
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in URL [bundleentry://860.fwk10039797/META-INF/spring/client-context.xml]: Cannot resolve reference to bean 'jpaVendorAdapter' while setting bean property 'jpaVendorAdapter'; nested exception is org.springframework.beans.factory.CannotLoadBeanClassException: Cannot find class [org.springframework.orm.jpa.vendor.EclipseLinkJpaVendorAdapter] for bean with name 'jpaVendorAdapter' defined in URL [bundleentry://860.fwk10039797/META-INF/spring/client-context.xml]; nested exception is java.lang.ClassNotFoundException: org.springframework.orm.jpa.vendor.EclipseLinkJpaVendorAdapter not found from bundle [client]
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:328)
```
Here's a little test I did real quick if you're interested:
```
public class TestOsgi extends AbstractConfigurableBundleCreatorTests
{
    @OSGi
    public void testSimpleLoad()
    {
        System.out.println(bundleContext);
    }
}
```
I've also checked Maven Central to make sure everything was up to date. If I'm doing something wrong please let me know! I'm open to opinions/suggestions!

---

