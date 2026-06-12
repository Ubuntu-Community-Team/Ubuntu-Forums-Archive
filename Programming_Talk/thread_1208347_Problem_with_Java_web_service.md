---
title: "Problem with Java web service"
date: 2009-07-09
forum: Programming Talk
---

### Post by tashe on 2009-07-09
I am trying to connect my REST web service to a Oracle DB. I have ojdbc14-10.2.0.2. When I run the webapp that uses my service and try to get data from the DB it displays the error. I did connect successfully to the same DB with the same code and driver but from a regular Java desktop app. For the REST service we are using Jersey. 

```
HTTP Status 500 - 

--------------------------------------------------------------------------------

type Exception report

**message **

**description **The server encountered an internal error () that prevented it from fulfilling this request.

**exception **

javax.servlet.ServletException: java.lang.NoClassDefFoundError: oracle/jdbc/pool/OracleDataSource
	com.sun.jersey.spi.container.servlet.WebComponent.service(WebComponent.java:311)
	com.sun.jersey.spi.container.servlet.ServletContainer.service(ServletContainer.java:425)
	com.sun.jersey.spi.container.servlet.ServletContainer.service(ServletContainer.java:590)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)


**root cause **

com.sun.jersey.api.container.MappableContainerException: java.lang.NoClassDefFoundError: oracle/jdbc/pool/OracleDataSource
	com.sun.jersey.server.impl.model.method.dispatch.ResourceJavaMethodDispatcher.dispatch(ResourceJavaMethodDispatcher.java:74)
	com.sun.jersey.server.impl.uri.rules.HttpMethodRule.accept(HttpMethodRule.java:166)
	com.sun.jersey.server.impl.uri.rules.ResourceClassRule.accept(ResourceClassRule.java:74)
	com.sun.jersey.server.impl.uri.rules.RightHandPathRule.accept(RightHandPathRule.java:114)
	com.sun.jersey.server.impl.uri.rules.RootResourceClassesRule.accept(RootResourceClassesRule.java:66)
	com.sun.jersey.server.impl.application.WebApplicationImpl._handleRequest(WebApplicationImpl.java:658)
	com.sun.jersey.server.impl.application.WebApplicationImpl.handleRequest(WebApplicationImpl.java:616)
	com.sun.jersey.server.impl.application.WebApplicationImpl.handleRequest(WebApplicationImpl.java:607)
	com.sun.jersey.spi.container.servlet.WebComponent.service(WebComponent.java:309)
	com.sun.jersey.spi.container.servlet.ServletContainer.service(ServletContainer.java:425)
	com.sun.jersey.spi.container.servlet.ServletContainer.service(ServletContainer.java:590)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)


```

Does anyone have an idea what causes this error? thanks

---

### Post by jespdj on 2009-07-09
It looks you are missing some classes in the classpath. Make sure that all the JAR files you need (especially the Oracle JDBC driver JAR) are available.

If this is a web application (WAR file), put the JAR file in WEB-INF/lib inside your WAR file.

---

### Post by tashe on 2009-07-09
Thanks for you quick reply
This is a Eclipse project and I run it from there. I haven't used any war files to run it on server. I just make a right click and Run on Server. The server is Apache Tomcat 5.5. I have the jdbc driver imported in the project. But it still gives me error. 

A few minutes ago i read that i should copy the driver into common/lib folder of my Tomcat server. I did so and all the errors dissapeared, except that I dont get any rows from the DB. Do you think that this problem is now solved and I should try and resolve why I dont get rows. Or did it just fooled me and the error is not solved, but it just doesn't show it?
i hope you understand what i mean.

Also I tried to create a CLASSPATH enviroment variable which points to the jdbc driver, but that didn't help.
thanks for your help

---

