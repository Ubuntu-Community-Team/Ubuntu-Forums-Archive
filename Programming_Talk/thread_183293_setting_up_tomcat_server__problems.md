---
title: "setting up tomcat server / problems"
date: 2006-05-27
forum: Programming Talk
---

### Post by lakluster on 2006-05-27
Ok I am running Breezy Badger and I am having some problems getting my tomcat server to run correctly, heres what i've got so far.

I originally installed j2ee 1.4 but I decided it would just be easier to run a tomcat server to develop some servlets so I have now installed jdk1.5, JAVA_HOME is set correctly, java version 1.5 so tomcat is happy enough to start and run.  I have no problem running jsp pages or mapped servlets... however whenever I try to use my already made mysql DB connector classes I run into problems.  Let me just say the project I am trying to get running on here is just a simple jsp/servlet program that uses a mysql db.  It works 100% on my xp laptop running tomcat and has no problem accessing a mysql db.  However now it for some reason it has some problems.

The source of the problems: inside my database connector class when I get to establishing a connection with DriverManager I get a nullpointer exception.

```
conn = DriverManager.getConnection(url, user, pass);
```

I am positive it is not just a mysql connection error as I can connect fine with the details I am using in my db connector class in a php application and via command line.

I am importing all I need to as the same class works fine on fedora core 5 and xp, however I must be missing a file somewhere in my current java installation.  I am at a loss as to how to fix this problem so I am hoping someone a little more proficient in this area might be able to shed some light and maybe point me in the right direction.

Any help or suggestions would be appreciated!

---

### Post by yaaarrrgg on 2006-05-27
have you installed the mysql jdbc driver ?

[http://www.mysql.com/products/connector/j/](http://www.mysql.com/products/connector/j/)
[http://dev.mysql.com/doc/refman/5.0/en/cj-tomcat-config.html](http://dev.mysql.com/doc/refman/5.0/en/cj-tomcat-config.html)

---

### Post by lakluster on 2006-05-27
installed? No.  However, in each of my application's WEB-INF folder (../tomcat/webapps/app/WEB-INF) lib folder I have a similar mysql-connector-java-xxx.jar file.  It is an older version, but again it runs my applications fine on fc5 and xp running tomcat.  As far as installing the connector through including 3rd party libaries in tomcat the only way I know how to do that is the method I am using at the moment and it worked until I tried to move it to ubuntu.

Perhaps, simply adding to my applications WEB-INF/lib folder is not doing it on ubuntu?  If there is another way please let me know.

Thanks for the reply.

edit: also, I don't get any class not found exceptions when trying to use DriverManger which is from the jdbc library, so I would assume it is finding it... but for some reason throws an exception as if it was unable to connect to my mysql db (which could not be due to wrong host/user/pass as I have verified far to many times that what I have in my servlet file works when connecting to my mysql server through a command line).

---

### Post by yaaarrrgg on 2006-05-28
well, you can also put it in the common/lib folder, but i don't think that is the problem.  sounds like it is finding the jar.

actually, i remember having a problem like this a while back.  I had better luck passing in the username and password all through the url connection string, such as:

```

<%
//Load the MySql Driver.
Class.forName("com.mysql.jdbc.Driver");

//Make the Connection to the database.
String host = "localhost:3306";
String db = "test";
String user = "YOUR_DB_USERNAME";
String password = "YOUR_DB_PASSWORD";

String url = "jdbc:mysql://" + host + "/" + db + "?user=" + user + "&password=" + password ;

java.sql.Connection connection=
        java.sql.DriverManager.getConnection(url);

//Get SQL Statement.
java.sql.ResultSet rs=connection.createStatement().executeQuery("select * from example");

//Just get the first column's name of the table
String colName=rs.getMetaData().getColumnLabel(1);
out.println("col label is "+colName);

//For each row, get the first column and print it out
while(rs.next()){
Object o=rs.getObject(colName);
out.println(colName+" "+o);
}

%>

```

---

### Post by jvictor on 2006-05-28
Adding the jar into WEB-INF/lib must do, however add the jar to ur classpath variable and try

---

### Post by lakluster on 2006-05-28
[QUOTE=yaaarrrgg]well, you can also put it in the common/lib folder, but i don't think that is the problem.  sounds like it is finding the jar.

actually, i remember having a problem like this a while back.  I had better luck passing in the username and password all through the url connection string, such as:

```

<%
//Load the MySql Driver.
Class.forName("com.mysql.jdbc.Driver");

//Make the Connection to the database.
String host = "localhost:3306";
String db = "test";
String user = "YOUR_DB_USERNAME";
String password = "YOUR_DB_PASSWORD";

String url = "jdbc:mysql://" + host + "/" + db + "?user=" + user + "&password=" + password ;

java.sql.Connection connection=
        java.sql.DriverManager.getConnection(url);

//Get SQL Statement.
java.sql.ResultSet rs=connection.createStatement().executeQuery("select * from example");

//Just get the first column's name of the table
String colName=rs.getMetaData().getColumnLabel(1);
out.println("col label is "+colName);

//For each row, get the first column and print it out
while(rs.next()){
Object o=rs.getObject(colName);
out.println(colName+" "+o);
}

%>

```[/QUOTE]

I tried using your example above... I have never done the string url with everything in it before... is the string url in correct format?  I used my login information as well as updating my jdbc library to the newest version 3.1.12 (newest on the page you listed above) and I still get an exception thrown when it gets to the DriverManager.getConnection()... with your code I get a much better stack trace and the message I get back is java.net.ConnectException: Connection refused.  I must be missing something else as I can take the exact information I am providing in the jsp/servlet files and go, mysql -uusername -p -h localhost , and connect just fine! no problems.

What could I be doing wrong?

---

### Post by yaaarrrgg on 2006-05-28
That example works for me (tested on ubuntu).  I tested with tomcat 5, mysql 4.1.12 and put the jdbc jar in the common/lib folder.

Although it's starting to more like a permissions problem to me.  It sounds like mysql (or a firewall??) is blocking the connection for some reason.  Is it saying something like "connection refused for user@somehost ..."?  

To test this, you might try  lowering the server security, just for testing.  For example, you might try accepting '%' for hosts in the mysql permission table.  Are you adding users with the GRANT statement?  I have less trouble with it, than manually adding them to the tables..

Also, might try running tomcat in a "sudo -i" shell.

---

### Post by lakluster on 2006-05-29
[QUOTE=yaaarrrgg]That example works for me (tested on ubuntu).  I tested with tomcat 5, mysql 4.1.12 and put the jdbc jar in the common/lib folder.

Although it's starting to more like a permissions problem to me.  It sounds like mysql (or a firewall??) is blocking the connection for some reason.  Is it saying something like "connection refused for user@somehost ..."?  

To test this, you might try  lowering the server security, just for testing.  For example, you might try accepting '%' for hosts in the mysql permission table.  Are you adding users with the GRANT statement?  I have less trouble with it, than manually adding them to the tables..

Also, might try running tomcat in a "sudo -i" shell.[/QUOTE]
Well, I put the jdbc jar in the common/lib folder and that has yet to solve it.

As far as I know I have no firewall running... I can ssh/ftp to my ubuntu computer from a remote computer as well as run php applications that connect to the same mysql db I am trying to connect/use in jsp.  The only exception it gives me is the Connection refused, no other information other than that aside from a long stack trace.

Currently I have in my mysql/user table % set up as a host.  If you are talking about setting that some place else then I have not done that and would need a little direction on how to do so.  The host % was added via phpmyadmin.

I also tried running tomcat through sudo -i... I get no errors, but then again I get just a blank page for everything even on the default tomcat welcome page at localhost:8080/.

---

### Post by yaaarrrgg on 2006-05-29
Hmm, I guess the problem is with tomcat or java.  I tested this at home, and did these steps:

installed jdk1.5 with automatix (setting up manually is a little timeconsuming ... last time I had to manually unpack a couple jars in the debian package from sun)

downloaded an unpacked the newest tomcat 5.  changed permissions to chmod 775 bin/* 

and then started the servre with something like:

sudo -i
cd tomcat/bin/
export SET JAVA_HOME=/usr/lib/j2sdk1.5-sun/
./startup.sh

I could hit the [http://localhost:8080/](http://localhost:8080/) with no problems.  

I think  I am stumped :)  what does the stack trace look like?

Is the tomcat server fairly clean?  Sometimes I see problems on JBoss (with the j2ee compliant classloader configuration),  where if two classes are loaded with teh same name in the server, things will fail without given any good error message.  Might want to test everything with a stripped down, fresh install.

---

### Post by lakluster on 2006-05-29
from a fresh version of tomcat5 with permissions set and sudo -i and all I still Connection Refused... I seriously have no idea.

I tried installing jdk1.5 through automatix.... but after it gets done downloading it just hangs on installing for over 2 hours and there is no way that is right.  I already have the same j2sdk1.5-sun installed... I used the rpm release from sun's site and used the java-package (I think) and something else to turn that into a deb package that installed it for me.

Apparently it is something that ive done wrong... so I think I am just going to do a clean installed of ubuntu and start over :/

---

### Post by lakluster on 2006-05-29
ok so clean install of ubuntu 5.10.............

apache2, php, mysql all setup.  My php scripts that use a mysql db are working fine, mysql user permissions set.

I tried, again, to install jdk1.5 with automatix and again it downloaded the .deb file and hug at installing for over 2 hours (I would assume that is not normal as I can do sudo dpkg -i sun-j2sdk1.5_1.5.0+update05_i386.deb and it installs in less than 30 seconds.  I set the default java to the jdk1.5.. so java -version => jdk1.5.

I downloaded a new jdbc and put it in the common/lib folder, downloaded a new tomcat and extracted... it is currently located at /home/mike/tomcat5.  I chmod'd tomcat5/bin to 775 and then I run what you suggested:

sudo -i
cd ...
export ..
./startup.sh

Everything loads fine, I can view the default localhost:8080 fine, but as soon as any of my files tried to access a database => null pointer connection refused.

I kind of feel like the 3 hours I just spent reformating and simplying installing only the basics to get this thing to work has been a complete waste as it still doesnt work and I now lost everything else I had on it....

What could I possibly be doing or not doing to cause it to not work for me and yet work flawlessly for you?

---

### Post by lakluster on 2006-05-29
ok, so more progress.  A little more messing and I tried your above example to connect to my database and got the following error/stacktrace:

> javax.servlet.ServletException: null,  message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
	org.apache.jasper.runtime.PageContextImpl.doHandlePageException(PageContextImpl.java:858)
	org.apache.jasper.runtime.PageContextImpl.handlePageException(PageContextImpl.java:791)
	org.apache.jsp.test_jsp._jspService(test_jsp.java:77)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)

I have localhost, %, and even the localhost.localdomain associated with the host column of the user/pass I am using to connect to the db.  Perhaps I am adding them wrong here?  I am hoping this is the only error left to get it to work...

---

### Post by lakluster on 2006-05-29
success!

fix: I switched the order in /etc/hosts to 127.0.0.1 localhost localhost.localdomain .

fixed the problem, go figure.

also thanks yaaarrrgg for your help :)

---

### Post by yaaarrrgg on 2006-05-29
glad you got it working :)

---

### Post by larry007 on 2006-06-26
I am trying to set up some software using Postgresql.  

I have the following results:
1. tomcat starts fine at bootup, displays localhost:8180, fine
2. I compiled the software (Dspace) as user, fine 
3. copied the .war files, fine
4. accessing the site I get an error:

"the server encountered an internal error() that prevented it from fulfilling the request"

logs reveal:
"java.security.AccessControlException: access denied (java.util.PropertyPermission dspace.configuration read)"
"... checkPermission(AccessControlContext.java:264)"
"... checkPermission(AccessController.java:427)"

I do realize that this information is suppose to help me solve the problem, but I have no clue as to what this means.  I changed the permissions on all the directories, but that didn't change anything...

PLEASE HELP!!

---

