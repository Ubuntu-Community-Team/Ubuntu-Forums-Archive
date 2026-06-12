---
title: "Syntax for JTDS JDBC Driver"
date: 2007-10-02
forum: Programming Talk
---

### Post by Black Mage on 2007-10-02
I'm using JTDS JDBC to connection to my SQL Server with syntax

```

con = DriverManager.getConnection(
		        "jdbc:jtds:sqlserver://192.168.1.216[:1433][/master]"
		        		);
//this is how its listed on their site
jdbc:jtds:<server_type>://<server>[:<port>][/<database>][;<property>=<value>[;...]]

```
So am I just putting it in completly wrong?

Has anyone used this before and has an example of the correct syntax?

---

### Post by ynnhoj on 2007-10-02
i'm pretty sure that the square brackets in the example are only there to show that those bits are optional.  i think that..
```
"jdbc:jtds:sqlserver://192.168.1.216:1433/master"
```
..might be more appropriate.

---

