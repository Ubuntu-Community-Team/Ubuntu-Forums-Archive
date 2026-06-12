---
title: "Spring Integration test: type mismatch for properties"
date: 2010-02-08
forum: Programming Talk
---

### Post by andrew222 on 2010-02-08
I hope you can help me with a problem I am having with running a Spring integration test using AbstractTransactionalSpringContextTests to wire my dependencies.  After everthing was wired correctly, I started getting some new errors telling me that some of the values injected read from .properties files were having a type mimatch.  When the web application runs. these errors never appear.

This is the error I was getting:

> org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'messageSource' defined in class path resource [siebel-test-context.xml]: Initialization of bean failed; nested exception is org.springframework.beans.TypeMismatchException: Failed to convert property value of type [java.lang.String] to required type [int] for property 'cacheSeconds'; nested exception is java.lang.NumberFormatException: For input string: "${dcla.external.properties.cache.second}"
Caused by: org.springframework.beans.TypeMismatchException: Failed to convert property value of type [java.lang.String] to required type [int] for property 'cacheSeconds'; nested exception is java.lang.NumberFormatException: For input string: "${dcla.external.properties.cache.second}"
Caused by: java.lang.NumberFormatException: For input string: "${dcla.external.properties.cache.second}"
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:48)
	at java.lang.Integer.parseInt(Integer.java:468)
	at java.lang.Integer.valueOf(Integer.java:547)
	at java.lang.Integer.decode(Integer.java:908)
	at org.springframework.util.NumberUtils.parseNumber(NumberUtils.java:146)
	at org.springframework.beans.propertyeditors.CustomNumberEditor.setAsText(CustomNumberEditor.java:114)
	at org.springframework.beans.TypeConverterDelegate.doConvertTextValue(TypeConverterDelegate.java:343)
	at org.springframework.beans.TypeConverterDelegate.doConvertValue(TypeConverterDelegate.java:319)
	at org.springframework.beans.TypeConverterDelegate.convertIfNecessary(TypeConverterDelegate.java:192)
	at org.springframework.beans.TypeConverterDelegate.convertIfNecessary(TypeConverterDelegate.java:138)
	at org.springframework.beans.BeanWrapperImpl.convertForProperty(BeanWrapperImpl.java:380)



In a properties file titled 'operations.properties' the value for ${dcla.external.properties.cache.second} is listed as:

dcla.external.properties.cache.second=120


Now, if I hard code the value in the Spring context configuration file, like this

<property name="cacheSeconds" value="120" />

....it will stop complaining about this value and then complain about another value which Spring says it can not convert from Date to String...


When the application runs on it's own, there is no need for a property editor.  Can there be something I can do to get these mismatch errors to stop?  Is there something I am doing wrong?

 
	```

```

---

