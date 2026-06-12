---
title: "MS acccess database from java"
date: 2006-10-23
forum: Programming Talk
---

### Post by kno712 on 2006-10-23
I'm trying to connect to a MS Access database and I want to do this through a standalone java program. There are some java examples on the web on how
to do this but they are for a  MS platform, they don't tell you that and lead you to think it is a solution. One of these examples above:


```

import java.sql.*;
public class test


    {
    public static void main(String[] args) 


        {
        // change this to whatever your DSN is
        String dataSourceName = "/database/mydatabase.mdb";
        String dbURL = "jdbc:odbc:" + dataSourceName;
        try { 
        Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
        Connection con = DriverManager.getConnection(dbURL, "",""); 
    }


        catch (Exception err) {
        System.out.println( "Error: " + err );
    }

}

}

```

Can you tell me if there is a way to do this? Any web resource where I can find how to do it?

Many thanks to all

---

