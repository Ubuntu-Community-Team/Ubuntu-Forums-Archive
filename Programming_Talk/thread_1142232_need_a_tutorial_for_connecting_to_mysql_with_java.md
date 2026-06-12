---
title: "need a tutorial for connecting to mysql with java"
date: 2009-04-29
forum: Programming Talk
---

### Post by kb2tfa on 2009-04-29
I'm looking for a straight forward way to connect to my mysql server with java

seems to be a very convoluted subject.

---

### Post by cabalas on 2009-04-29
Connecting to a mysql database isn't too hard in java, I have a quick example that shows you how to connect and preform a query.

The example is overly complicated, it is just a function from a fictional class:

[PHP]
void example(String address, String port, String dbName, String username, String password, String sql) {
	String dbURL = "jdbc:mysql://" + address + ":" + port + "/" + dbName;

	java.sql.Connection connection = java.sql.DriverManager.getConnection(dbURL, username, password);

	java.sql.Statement statement = connection.createStatement();
	java.sql.ResultSet res = s.executeQuery(sql);

	// Do something with result

	connection.close();
}
[/PHP]

Just note that in this example I haven't added in any error checking and I think pretty much every class/function in the example throws an exception.

The only thing that is kind of confusing is the first part of the dbURL

```
jdbc:mysql://
```

The first part is saying that the uri is a java database connection and the second in what type of database.

Hopefully that is understandable enough, if it isn't sorry I'll try and clear up any issues you have with it.

---

### Post by sujoy on 2009-04-29
however, manually managing database connections can be daunting, take a look at hibernate.

---

