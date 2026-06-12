---
title: "JSP/MySQL exception on executeUpdate() command?!"
date: 2010-08-13
forum: Programming Talk
---

### Post by osomphane on 2010-08-13
statement.executeUpdate(QueryString);

I followed a couple of tutorials, which all seem to have the following code in common. My problem is that whenever I try to run it, it throws an exception.

The exception happens on "statement.executeUpdate(QueryString);" but the SQL is correct and i've tried it on mysql's command line. Can anyone help out?

I'm using the latest MySQL, Netbeans, JDK, and Tomcat...

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<%@ page import="java.sql.*" %>
<%@ page import="java.io.*" %>
<html>
    <head>
        <title>display data from the table using jsp</title>
    </head>
    <body>
<%
    String connectionURL = "jdbc:mysql://localhost:3306/reorder?user=root&password=mypass";
    Connection connection = null;
    Statement statement = null;
    String QueryString = "CREATE TABLE Student (Name CHAR(10),StudentNumber INT, Class INT, Major CHAR(10))";
 
    try {
        Class.forName("com.mysql.jdbc.Driver").newInstance();
        connection = DriverManager.getConnection(connectionURL);
        statement = connection.createStatement();
        statement.executeUpdate(QueryString);
        } catch (Exception ex) {out.println("error");}
 
 
%>
    </body>
</html>
```

---

### Post by Some Penguin on 2010-08-13
The obvious thing to do would be to actually show the exception message and stack trace instead of throwing it away.

---

### Post by osomphane on 2010-08-13
Sorry, I'm a newbie with stack traces... Does it sound like I need to install a driver?

**out.println(ex.getMessage());**
com.mysql.jdbc.Driver

**ex.printStackTrace(new PrintWriter(out));**
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1516) at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1361) at org.apache.jasper.servlet.JasperLoader.loadClass(JasperLoader.java:128) at org.apache.jasper.servlet.JasperLoader.loadClass(JasperLoader.java:66) at java.lang.Class.forName0(Native Method) at java.lang.Class.forName(Class.java:169) at org.apache.jsp.installdb_jsp._jspService(installdb_jsp.java:71) at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70) at javax.servlet.http.HttpServlet.service(HttpServlet.java:717) at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:377) at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:313) at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:260) at javax.servlet.http.HttpServlet.service(HttpServlet.java:717) at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:290) at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:393) at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:233) at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:191) at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:127) at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102) at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109) at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:298) at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:852) at org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:588) at org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:489) at java.lang.Thread.run(Thread.java:619)

---

### Post by Some Penguin on 2010-08-13
From that, I'd suspect that the mysql JDBC connector jar file is nowhere in your webapps's WEB-INF/lib directory, because it's not even finding the class.

---

### Post by osomphane on 2010-08-13
Turns out even though NetBeans states compatibility with MySQL databases, you still need to install Connector/J by adding it as a library to the NetBeans IDE. When I deploy my application, would I have to set up Apache with Connector/J again or will that library be integrated in my project?

---

### Post by Some Penguin on 2010-08-13
Not familiar with NetBeans.  If the .jar is associated with a project's build path, I'd expect so.

You can find this out by unpacking the .war file (it's just a Zip archive with some extra files containing metadata) and seeing what's in that lib directory, however.

---

### Post by r-senior on 2010-08-14
> **osomphane said:**
> Turns out even though NetBeans states compatibility with MySQL databases, you still need to install Connector/J by adding it as a library to the NetBeans IDE.
Absolutely. The various Netbeans support libraries are pre-defined collections of JAR files that are packaged with the IDE and get added to the classpath. You have to selectively choose the libraries you need for a project. It would be unreasonable to have all libraries in by default.

For significant projects (and projects become "significant" quite quickly), managing these dependencies becomes troublesome. Maven is a great asset, once you get over the initial learning curve, and has excellent support built into the most recent versions of Netbeans.

---

