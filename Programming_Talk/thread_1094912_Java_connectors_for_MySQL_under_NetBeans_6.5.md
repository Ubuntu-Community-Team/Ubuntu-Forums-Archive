---
title: "Java connectors for MySQL under NetBeans 6.5"
date: 2009-03-13
forum: Programming Talk
---

### Post by gisse on 2009-03-13
Let start form beginning.

1. Installed Java 6 SDK
2. MySQL 5.1
3. Java connectors mysql-connector-java-5.0.8-bin.jar all done by book
4. Installed NetBeans 6.5 with GlassFish and TomCat also.

Now.

In IDE registered MySQL and connected to database, made new server resource and data pool. Deployed project with no problems. And then when i try to run program it show in browser:

```
HTTP Status 500 -

type Exception report

message

descriptionThe server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException: javax.servlet.jsp.JspException: Unable to get connection, DataSource invalid: "java.sql.SQLException: No suitable driver found for jdbc/IFPWAFCAD"

root cause

javax.servlet.jsp.JspException: Unable to get connection, DataSource invalid: "java.sql.SQLException: No suitable driver found for jdbc/IFPWAFCAD"

note The full stack traces of the exception and its root causes are available in the Sun Java System Application Server 9.1_02 logs.
Sun Java System Application Server 9.1_02
```

Also i have tried with this tutorial with simple copy/past in and adding necessary resources. [http://www.netbeans.org/kb/60/web/mysql-webapp.html#settingUpConnPool]("http://www.netbeans.org/kb/60/web/mysql-webapp.html#settingUpConnPool")

But all with same result. Is it problem in IDE or something is missing there in GlassFishV2?

---

### Post by Hotzero on 2009-10-21
Thank you man, I think this will solve my issue withe Netbeans

---

