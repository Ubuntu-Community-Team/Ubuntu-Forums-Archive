---
title: "Java &amp; SQL Server"
date: 2007-10-01
forum: Programming Talk
---

### Post by Black Mage on 2007-10-01
Hey,

Is there a recommended bridge or driver I should be using to connect Java in Ubuntu to a SQL 2000 Server?

---

### Post by Howler9443 on 2007-10-01
I'm using JTDS driver with SQLServer 2000 and it seems to work great.

[http://jtds.sourceforge.net/](http://jtds.sourceforge.net/)

I hope this helps.

---

### Post by Black Mage on 2007-10-01
Does your code look anything like this for connecting?

```

//Connect to the Database
			Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
			con = DriverManager.getConnection(
	        "jdbc:microsoft:sqlserver://192.168.1.216:1433");
	         stmt = con.createStatement();

```

---

