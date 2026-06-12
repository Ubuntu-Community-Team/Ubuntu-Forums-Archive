---
title: "Connect to database in Java"
date: 2010-09-22
forum: Programming Talk
---

### Post by Vistz on 2010-09-22
I have a website with a database set up. How would I connect to it using Java?

This is some code I found on another website
```
[COLOR=#7f0055][B]
public class MysqlConnect{
    public static void main(String[] args) {
        System.out.println("MySQL Connect Example.");
        Connection conn = null;
        String url = "jdbc:mysql://localhost:3306/";
        String dbName = "jdbctutorial";
        String driver = "com.mysql.jdbc.Driver";
        String userName = "root";
        String password = "root";
        try {
            Class.forName(driver).newInstance();
            conn = DriverManager.getConnection(url+dbName,userName,password);
            System.out.println("Connected to the database");
            conn.close();
            System.out.println("Disconnected from database");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}[/B][/COLOR][COLOR=#000000]
[/COLOR]
```Do I need to change the "driver" variable to something else in order to get this to work?

---

### Post by kahumba on 2010-09-22
> **Vistz said:**
>  How would I connect to it using Java?
[http://www.google.com/#sclient=psy&hl=en&q=Java+connect+to+mysql&aq=f&aqi=g4&aql=&oq=&gs_rfai=&pbx=1&fp=6f32b8af52b7e0b8](http://www.google.com/#sclient=psy&hl=en&q=Java+connect+to+mysql&aq=f&aqi=g4&aql=&oq=&gs_rfai=&pbx=1&fp=6f32b8af52b7e0b8)

---

### Post by Vistz on 2010-09-22
```

import java.sql.*;

public class Connect{
    public static void main(String[] args) {
        System.out.println("MySQL Connect Example.");
        Connection conn = null;
        [COLOR=#000000]String url = [/COLOR][COLOR=#2a00ff]"mysql15.000webhost.com/"[/COLOR][COLOR=#000000];[/COLOR]//I replaced this with my host name
        [COLOR=#000000]String dbName = [/COLOR][COLOR=#2a00ff]"a2609916_hscore"[/COLOR];//name of database
        [COLOR=#000000]String driver = [/COLOR][COLOR=#2a00ff]"com.mysql.jdbc.Driver"[/COLOR][COLOR=#000000];[/COLOR]//I left this as is
        [COLOR=#000000]String userName = [/COLOR][COLOR=#2a00ff]"root"[/COLOR][COLOR=#000000]; [/COLOR]//mysql user name
        [COLOR=#000000]String password = [/COLOR][COLOR=#2a00ff]"root"[/COLOR][COLOR=#000000];//password[/COLOR]
        try {
            Class.forName(driver).newInstance();
            conn = DriverManager.getConnection(url+dbName,userName,password);
            System.out.println("Connected to the database");
            conn.close();
            System.out.println("Disconnected from database");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```When I run the code above, I get an error, 
```
java.sql.SQLException: No suitable driver found for mysql15.000webhost.com/a2609916_hscore
```

---

### Post by Some Penguin on 2010-09-22
You haven't said whether you've downloaded an appropriate MySQL JDBC connector and placed the .jar in your classpath.

---

### Post by Vistz on 2010-09-22
> **Some Penguin said:**
> You haven't said whether you've downloaded an appropriate MySQL JDBC connector and placed the .jar in your classpath.

I've run this

```
sudo apt-get install libmysql-java
```

And I've placed "mysql-connector-java-5.1.10.jar" in my classpath"

---

### Post by wkhasintha on 2010-09-23
Make sure the jdbc driver is in the class path.

---

### Post by Some Penguin on 2010-09-23
It's also important to not omit the jdbc:mysql part of the URI.

---

### Post by Vistz on 2010-09-23
I still get an error even after I change the url

```
String url = "jdbc:mysql//mysql15.000webhost.com/";
```

---

### Post by r-senior on 2010-09-23
Your URL should look more like this:

```
jdbc:mysql://hostname:3306/databasename
```

3306 is the default port for MySQL but you might want to verify that's correct in your case.

---

