---
title: "JSP Import Jar in Tomcat"
date: 2010-04-19
forum: Programming Talk
---

### Post by huangyingw on 2010-04-19
Hello,
    I encountered a problem at JSP.
    At my jsp file:"result.jsp", I need to use these two jar files
    ```

    /media/volgrp/myproject/git/webapps/luceneweb/WEB-INF/lib/lucene-core-3.0.1.jar:/media/volgrp/myproject/git/webapps/luceneweb/WEB-INF/lib/lucene-demos-3.0.1.jar
    
```
    , so I import them through
    ```

    <%@ page import = "    org.apache.lucene.store.*" %>
    
```
    And I update my /etc/profile:
    ```

    CLASSPATH=/media/volgrp/myproject/git/java/lucene/lucene-3.0.1/lucene-core-3.0.1.jar:/media/volgrp/myproject/git/java/lucene/lucene-3.0.1/lucene-demos-3.0.1.jar:/media/volgrp/myproject/git/webapps/luceneweb/WEB-INF/lib/lucene-core-3.0.1.jar:/media/volgrp/myproject/git/webapps/luceneweb/WEB-INF/lib/lucene-demos-3.0.1.jar
		export CLASSPATH
    
```
    After rebooting Ubuntu, I still got this exception when requesting:
    ```

    http://localhost:8080/luceneweb/results.jsp?query=linux&maxresults=100
    
```
    ```

    exception 
org.apache.jasper.JasperException: javax.servlet.ServletException: java.lang.NoClassDefFoundError: Could not initialize class org.apache.lucene.store.FSDirectory
    
```

---

### Post by Some Penguin on 2010-04-19
Have you actually read the Tomcat documentation?  There's a specific place where CLASSPATH gets set, if memory serves.

You also shouldn't randomly include whitespace in attribute values.

---

### Post by myrtle1908 on 2010-04-19
Best to put your app specific JARs in the WEB-INF/lib folder.  No need to mess with classpath etc.

---

