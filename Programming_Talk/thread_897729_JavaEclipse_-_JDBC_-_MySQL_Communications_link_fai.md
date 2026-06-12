---
title: "Java/Eclipse - JDBC - MySQL: Communications link failure"
date: 2008-08-22
forum: Programming Talk
---

### Post by *malagant* on 2008-08-22
hi, 
maybe someone can help me with my programming problem :/

```

import java.sql.*;

public class test2 {
	public static void main(String[] args) throws Exception {
		Class.forName ("com.mysql.jdbc.Driver").newInstance ();
		Connection conn = DriverManager.getConnection ("jdbc:mysql://<my_hostname>/<my_database>", "<my_username>", "<my_password>");
		conn.close();
	}
}

```

And the result:

```

Exception in thread "main" com.mysql.jdbc.CommunicationsException: Communications link failure

Last packet sent to the server was 0 ms ago.
at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1070)
at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2104)
at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:729)
at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:298)
at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:283)
at java.sql.DriverManager.getConnection(libgcj.so.81)
at java.sql.DriverManager.getConnection(libgcj.so.81)
at test2.main(test2.java:6)
Caused by: java.io.CharConversionException
at gnu.gcj.convert.Input_iconv.read(libgcj.so.81)
at java.lang.String.init(libgcj.so.81)
at java.lang.String.<init>(libgcj.so.81)
at com.mysql.jdbc.SingleByteCharsetConverter.<init>(SingleByteCharsetConverter.java:153)
at com.mysql.jdbc.SingleByteCharsetConverter.initCharset(SingleByteCharsetConverter.java:108)
at com.mysql.jdbc.SingleByteCharsetConverter.getInstance(SingleByteCharsetConverter.java:86)
at com.mysql.jdbc.ConnectionImpl.getCharsetConverter(ConnectionImpl.java:2767)
at com.mysql.jdbc.StringUtils.getBytes(StringUtils.java:681)
at com.mysql.jdbc.Buffer.writeStringNoNull(Buffer.java:665)
at com.mysql.jdbc.Buffer.writeString(Buffer.java:639)
at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1287)
at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2032)
...6 more

```

I'm using Ubuntu, Eclipse SDK 3.2.2 and the JDBC driver for MySQL that comes via the paketmanager (v5.1.5).

I added /usr/share/java/mysql-connector-java-5.1.5.jar to the Build Path as an external JAR.

The error message appears while using java-1.5.0-gcj-4.2-1.5.0.0.
 I tried java-6-sun-1.6.0.06 and openjdk as well, but with both JREs, the program just hangs up, without throwing an exception.

It is not a problem with the database, i can connect from Windows without a problem, and using the MySQL Administrator tool, i can connect from Linux as well. So it must be a problem with JDBC (?).

Does anyone have an idea? :)

---

### Post by tinny on 2008-08-22
1. Is this a web application? If so put your db driver jar in the WEB-INF/lib/ folder

2. In your my.cnf file (on your MySQL server) is your MySQL bound to 127.0.0.1? Comment out bind-address=127.0.0.1

3. Do you have MySQL GUI tools installed (available in the repositories)? Try and connect to this DB using MySQL GUI tools from the same host that your program is running from.

BTW: stick with the Sun Java 6 JDK

---

### Post by drubin on 2008-08-22
> **tinny said:**
> btw: Stick with the sun java 6 jdk
+1

---

### Post by *malagant* on 2008-08-23
Ok thanks, i finally solved my problem. I used java-6-sun-1.6.0.06 instead of java-1.5.0-gcj-4.2-1.5.0.0 as JRE and imported the mysql-connector-java-5.1.6-bin.jar as a external JAR from [http://dev.mysql.com/downloads/connector/j/5.1.html](http://dev.mysql.com/downloads/connector/j/5.1.html) and not the broken(?) 5.1.5 that comes via the paket manager.

---

### Post by theirishfozz on 2008-10-01
Odd, I have this problem too. I cant even connect to the db (I can from the shell and mysql administrator). The difference is I've been using the "un-broken" jar the whole time so it must have been something else you changed.

EDIT: AHA..I was using port 3309 instead of 3306 to connect.

---

### Post by Kastenfrosch on 2009-07-15
I got the same Problem in my Java-Project.
My fault was, that i created a SecurityManager, but didn't start the java Machine with the option -DJava Security Manager (...)


hope that helps someone :).
:guitar:

---

