---
title: "J2EE: problem with ResultSet in DAO"
date: 2009-05-27
forum: Programming Talk
---

### Post by andrew222 on 2009-05-27
This is code in a DAO for a web based application...

The DB I am using is MS Access and the connection is successful.  After the line:

```
rs = ps.executeQuery();

```

This code should execute, but the "result set is null" println statement will not even print...

```

 // Will not print out below this line
 if (rs == null)
System.out.println("result set is null");
```

Here is the segment of code from the DAO


```

Connection conn = null;
ResultSet rs =null;
PreparedStatement ps =null;

try
{
conn = DataSourceManager.getConnection();

if(conn==null)
{
 System.out.println("connected");
}
else
System.out.println("connected");


String userID = "700001";

ps = conn.prepareStatement("select * from AG_Account where Account.Person_ID=?");

if(ps==null)
{
System.out.println("prepared statement is null");
}

ps.setString(1,userID);

rs = ps.executeQuery();


// Will not print out below this line
 if (rs == null)
System.out.println("result set is null");


rs.last();

int row = rs.getRow();
}

catch(SQLException se)
{
 se.toString();
}

catch(Exception e)
{
 e.toString();
}

finally
{
   close(rs,conn,ps);
}


```


I can't seem to figure out why this is happening.

I need to know where to look and to know why this would happen.   I suspect it may be with the SQL query...

---

