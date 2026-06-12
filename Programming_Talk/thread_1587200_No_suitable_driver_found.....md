---
title: "No suitable driver found...."
date: 2010-10-03
forum: Programming Talk
---

### Post by oontvoo on 2010-10-03
I was coding this simple program using NETBEAN.
```

public class Simple
{
    // Database URL
 [COLOR="Navy"]   static final String DATABASE_URL = "JDBC:MYSQL://localhost/books";[/COLOR]


    public static void main(String[] args)
    {
        Connection connection = null;
        Statement statement = null;
        ResultSet resultSet = null;

        // connect to database books and query database
        try
        { .....

```

I kept getting this error msg
> java.sql.SQLException: No suitable driver found for JDBC:MYSQL://localhost/books

Any idea how to resolve this problem?

---

### Post by r-senior on 2010-10-03
Have you tried:

```
static final String DATABASE_URL = "jdbc:mysql://localhost/books";
```

If you then get a ClassNotFoundException, you need to make sure you have the MySQL [JDBC Driver](http://www.mysql.com/downloads/connector/j/) on your classpath.

I'm assuming you are loading the JDBC driver (with Class.forName or DriverManager.registerDriver) in the code that we can't see.

---

### Post by Some Penguin on 2010-10-03
Why so upper-case?

---

### Post by oontvoo on 2010-10-04
> **r-senior said:**
> Have you tried:

```
static final String DATABASE_URL = "jdbc:mysql://localhost/books";
```

If you then get a ClassNotFoundException, you need to make sure you have the MySQL [JDBC Driver](http://www.mysql.com/downloads/connector/j/) on your classpath.

I'm assuming you are loading the JDBC driver (with Class.forName or DriverManager.registerDriver) in the code that we can't see.

I tried adding "static final" to the code. It still didn't change anything. About the MySQL JDBC Driver, I'm pretty sure I have it. But just to be sure, how'd I check that?

Well, I'm sorry but what do you mean by > make sure you have the MySQL [JDBC Driver](http://www.mysql.com/downloads/connector/j/) on your classpath.? I suppose you're saying I need to add the path to the JDBC driver to the commandline. Am I correct? Well, if that's the case, then I didn't run my java app from the command-line. I compiled and ran it with the IDE (NetBean 6 something). 

Honestly, I'm very new to Java....

---

