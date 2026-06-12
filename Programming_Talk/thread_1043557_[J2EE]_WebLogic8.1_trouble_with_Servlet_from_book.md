---
title: "[J2EE] WebLogic8.1 trouble with Servlet from book"
date: 2009-01-18
forum: Programming Talk
---

### Post by andrew222 on 2009-01-18
Hello,

I downloaded some code from coreservlets.com and put the code on BEA WebLogic 8.1.  The code is actually from ch4 of the book "Core Servlets and Java Server Pages (Hall/Brown)".  

I wanted to run a particular html form that one fills out then goes to a servlet.  The html form works just fine, it's just when I click on the form it is supposed to go to a servlet for output and instead I get a 'page not found message'.  The app built with no errors and deployed successfully...

Now, the line on the html form from the books says...

```
<FORM ACTION="./servlet/coreservlets.ThreeParams">
``` 

but since i am running it on WebLogic, the folder hierarchy is different. The only way I can get the code window to not say that the file exists (any other way it tells me that the page does not exist with a green line under it) is to write the line as so...

```
<FORM ACTION="./WEB-INF/classes/coreservlets/ThreeParams.class">
```


Can someone tell me what would have to be done in order to get the Servlet page to appear instead of an error message, the files i used from the book are attached to this thread as well in a zip file.

---

### Post by myrtle1908 on 2009-01-18
Not sure about BEA WebLogic but if it is a J2EE conforming servlet container (like Tomcat) then you should add the following to your web.xml

```
<servlet>
  <servlet-name>ThreeParams</servlet-name>
  <servlet-class>coreservlets.ThreeParams</servlet-class>
</servlet>
<servlet-mapping>
  <servlet-name>ThreeParams</servlet-name>
  <url-pattern>/ThreeParams</url-pattern>
</servlet-mapping>
```

obviously re-load your web app after editing the web.xml

and also change the form action to

```

<FORM ACTION="ThreeParams">
```

---

### Post by andrew222 on 2009-01-18
It worked with no fail. Thank you very much (I'll click a thanks as well).

Hope you have a good week...

---

