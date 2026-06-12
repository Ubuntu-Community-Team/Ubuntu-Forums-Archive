---
title: "New to JAVA.  Need help with DB Access."
date: 2019-06-30
forum: Programming Talk
---

### Post by rayj00 on 2019-06-30
Not sure if this is the place to ask this?  Not having any luck in various Java forums I've tried.

Anyway...

* Ubuntu 18.04 Server.
* Tomcat Version : Apache Tomcat/8.5.38
* Servlet Specification Version : 3.1
* JSP version : 2.3

java -version
openjdk version "11.0.3" 2019-04-16
OpenJDK Runtime Environment (build 11.0.3+7-Ubuntu-1ubuntu218.04.1)
OpenJDK 64-Bit Server VM (build 11.0.3+7-Ubuntu-1ubuntu218.04.1, mixed mode, sharing)

So I am playing with an evaluation copy of an Apache-Tomcat server application.

The application works as advertised in the default mode.  Great!

**Now I am trying to add a process to get a javascript variable and update a mysql database with it.** 
**I need to save a single javascript variable in a database.  This is because a subsequent client needs to be able to read it out of the database.**
  
So the app came with an index.html file. The top of the index.html file has the following line:

 <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

I have created the database WebRTCApp:

mysql> use WebRTCApp;
mysql> select * from broadcast;
+----+----------+
| id | streamID |
+----+----------+
|  1 | 7xh30n4xp08 |
+----+----------+
1 row in set (0.00 sec)

I am creating a random 11 character variable that I will use to define the streamID.

So, I thought I could accomplish what I need to do using Ajax and PHP, but the Apache-Tomcat server does not support using PHP.  I guess that leaves me with Java Servlets?

To sum it up, I have an app that runs under apache-tomcat.  I use javascript to create a random 11 character value and I need to store it in the mysql database.
This usage of apache-tomcat does not support PHP, so Ajax and php is out of the question.  Are Java servlets in order?
  
I've looked at many examples of java servlet usage but the more I look, the more confused I get.

Can anyone advise on how I can achieve, what appears to be simple task?
If you need additional information on this mysterious app, let me know.

However, the issue is strictly how apache-tomcat can store a javascript variable and to mysql.  And subsequently, a client retrieves the variable from the same database.

PS: I am not a programmer or coder per-se, show this old man a little compassion!  :)
Thanks,

---

### Post by Drenriza on 2019-07-02
A little information to help you out, i have not tested this and made on the fly so their might be a bug or two you need to sort out, let me know how it works :)
If you havent download the MySQL JDBC driver
[https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

Unpack the tar.gz and place the connector .jar file in /opt/tomcat/lib on the Tomcat server

In your web project either navigate to or create the path /WebContent/META-INF/context.xml
Note WebContent is the name of my root folder, for my projects.

In the context.xml file add the following
```
<Context antiResourceLocking="true">
<Resource name="jdbc/Test1" auth="Container" type="javax.sql.DataSource"
    maxTotal="20" maxIdle="5" maxWaitMillis="5000"
    username="YOUR USERNAME" password="YOUR PASSWORD" driverClassName="com.mysql.jdbc.Driver"
    removeAbandonedOnBorrow="true" logAbandoned="true"
    url="jdbc:mysql://IP_ADDRESS:3306/DATABASE_NAME"/>
</Context>
```

Create a new class, call it NewClass and add the following two methods
```
private synchronized java.sql.Connection openConnection() throws SQLException, FileNotFoundException, IOException, ClassNotFoundException, NamingException {
    Context initContext = new InitialContext();
    Context envContext = (Context) initContext.lookup("java:/comp/env");
    DataSource ds = (DataSource) envContext.lookup("jdbc/Test1");
    
    return ds.getConnection();
}

public String testOne() {
    try(Connection c = this.openConnection()) {
        String query = "SELECT * FROM TABLENAME";
        PreparedStatement ps = (PreparedStatement) c.preparedStatement(query);
      
        ResultSet rs = ps.executeQuery();
        String last = null;
        while(rs.next) {
            System.out.println("data: " + rs.getString(1));
            //See the output of System.out in catalina.out file on the tomcat server
            last = rs.getString(1);
        }
        
        return last;
    }
}
```

Make a new servlet, outside the doGet method instansiate the NewClass
NewClass nc = NewClass();

Edit the doGet method
```
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String url = "welcome.jsp";
        
        String MySQLString = nc.testOne();
        
        request.setAttribute("SQLString", MySQLString);
        getServletContext().getRequestDispatcher(url).forward(request, response);
}

```

make a welcome.jsp page and grab the MySQL value with Expression Language
<p>My MySQL value is ${SQLString}</p>

in web.xml make the servlet the welcome file and add the servlet mapping
```
<welcome-file-list>
<welcome-file>welcome.do</welcome-file>
</welcome-file-list>

<servlet>
<servlet-name>S1</servlet-name>
<servlet-class>YOUR.PATH.ServletNameWithoutDotJava</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>S1</servlet-name>
<url-pattern>/welcome.do</url-pattern>
</servlet-mapping>
```

My 2 cents. Much of this is project setup and very little is grabbing the actual value and displaying it.
I can recommend [https://www.murach.com/shop/murach-s-java-servlets-and-jsp-3rd-edition-detail](https://www.murach.com/shop/murach-s-java-servlets-and-jsp-3rd-edition-detail) if you need some solid reading

Please note, i do NOT consider myself a developer

---

