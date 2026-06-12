---
title: "JavaServerFaces: Validation?"
date: 2012-05-17
forum: Programming Talk
---

### Post by fallenshadow on 2012-05-17
Hi guys/gals,

I want to know how to do validation in JSF pages? I have created a JSF project and when you click the login button it will bring you to the welcome page.

However I need to check the login info obviously! :D

I have a (currently empty) class called validatePassword but I don't know what to do with it really.

In my login web page I have this:

```
<h:inputSecret value="#{loginBean.password}"><f:validator validatorId="com.test.ValidatePassword"/></h:inputSecret>
```

If this is correct then good, all I need to do is put something in my validatePassword file.

---

### Post by r-senior on 2012-05-17
I don't know the answer and I'm busy at the moment -- but look into JSR-303 validation. That is the way forward for validation in all Java web frameworks. JSF should have support for it by now.

You need a validator implementation in your classpath -- the Hibernate one is commonly used, even without Hibernate itself -- then you annotate your entity objects with validation and the web framework uses that information. It's a much better way of validating than doing it in the presentation part of the application because validation is centralised and close to the data.

---

### Post by fallenshadow on 2012-05-18
Ah thanks! I know its kinda in the wrong layer at the moment but I just wanted to play around with it first.

I added my JSF project stuff into my already working Java application project. However I have the most strange problem. The index.html page I created a long time ago keeps appearing instead of my login.xhtml.

It is really weird now as I have deleted that index.html entirely from the project but it keeps on appearing when I run it.

Check out this:

> 
<welcome-file-list>
    <!--  <welcome-file>index.html</welcome-file> 
    <welcome-file>index.htm</welcome-file> 
    <welcome-file>index.jsp</welcome-file>
    <welcome-file>default.html</welcome-file>
    <welcome-file>default.htm</welcome-file>
    <welcome-file>default.jsp</welcome-file> -->
    <welcome-file>login.xhtml</welcome-file>
  </welcome-file-list>


There is no way in hell that index.html should be able to appear but somehow it does even though it no longer exists! :shock:  ](*,)

---

### Post by fallenshadow on 2012-05-22
I got this fixed. I don't know why but it has stopped acting up and is working properly now. :D

---

